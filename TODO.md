## TODO

### Add run in debugger support

Add `npm-mode-npm-run-debug` command that will run a project script
under the node debugger, and bind it to <kbd>C-c n d</kbd> in mode
command keymap.

### Improve handling of exec buffers ###

At conclusion of running any npm command, the user is left in a
terminal buffer with a process attached. This requires the user to
<kbd>C-x k</kbd><kbd>y</kbd> to dispose of.

To the user, the fact that it ran in an ansi-term is irrelevant, and
being left it one at conclusion of operation is annoying. Rather than
presenting the user with a terminal buffer at all, why not just hook
up the buffer to the npm command's i/o streams. When the command ends,
we could then just display a status message and a `Press q to quit...`
message. When the user hits <kbd>q</kbd> the buffer would then be
killed leaving the user in the buffer they started in.