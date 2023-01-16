# sapcontrol-bash-completion

A simple (and incomplete) bash completion for the `sapcontrol` command.

The completion was generated by `completely` (https://github.com/DannyBen/completely) using `sapcontrol-completion.yaml` from this repository. If you want to make any changes you need to set up a `completely` environment and generate  a new `sapcontrol.completion` after making changes to `sapcontrol-completion.yaml`.

## Installation

### `bash`

Copy the completion script to the right place:

```
cp sapcontrol.completion /usr/share/bash-completion/completions/sapcontrol
```

After a re-login or sourcing that file, the completion should be available.


### `csh/tcsh`

The `tcsh` seems to have a different completion approach. If anybody knows a clean way, let me know.
Meanwhile I used https://github.com/marckhouzam/tcsh-completion to use the bash-completion in `tcsh`.
(The setup script `./setup-tcsh-completion.bash` can run a very very long time (On my SLES 15.3 VM 
around two minutes) without any output if there are a lot of existing bash completions.)

## Usage

After the command `sapcontrol` has been completed, press `-` followed by `<TAB>` to get all the suggestions.

**The current implementation (generated by `completely`) requires the dash, to present any suggestions.
Just `<TAB>` won't be enough.**

If it does not seem to work, check if the function `_sapcontrol_completions` is really part of your environment (`bash` only):

```
> set | grep ^_sapcontrol_completions
_sapcontrol_completions () 
_sapcontrol_completions_filter () 
```

If not, then check the steps described in "Installation" above.

## Limitations

The generated completion has some limitations:

- Options with multiple variable arguments (like `-repeat`) have at best only a completion
  for the first argument (limitation of shell globing).

- Options where no sensible suggestions are possible (like `-function ParameterValue [<parameter>]`) have no completion.

- If the meaning of an argument is not clear, no completion exists.\
  (People with deeper SAP knowledge may contribute here!)  

## To Do

- Fixing bugs and implement missing things (if people report them).
