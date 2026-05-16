# ABL Scratch Playground

A VS Code extension for writing ABL scratch files (a.k.a. Scratchpad / ABL Dojo).

## Related Software
This extension depends on the [OpenEdge ABL](https://marketplace.visualstudio.com/items?itemName=RiversideSoftware.openedge-abl-lsp) extension by [Riverside Software](https://marketplace.visualstudio.com/publishers/RiversideSoftware).

## Description
It lets you quickly create and run short Progress OpenEdge ABL sratch snippets.

The ABL Scratches view, which is automatically opened after installation, detects the OpenEdge projects in your workspace and allows each scratch to run in the context of a selected project.

To add a new scratch, use the action **New scratch** or click the **+** button. When the workspace has multiple OpenEdge projects, a drop-down is shown where you can pick the target OpenEdge project.

Scratch files are stored **inside** your project in the `.scratches` folder. When creating a scratch for the first time, you will be prompted to include `.scratches` to your `.gitignore` file (if the project uses Git).

## ABL Scratches view
The ABL Scratches view allows you to manage your scratch files. From this view you can create, open, run and delete scratches.
For each scratch, the last run timestamp is displayed in the list.
It's also possible to set a custom 'Description' to the scratch and to choose a different Mode (gui, chui, batch).

### Actions
- **New scratch**
  Creates a new scratch file and opens it in the editor
  Default keybinding: `Win+F3` (or `Cmd+F3` for macOS)
  _(Also available via the Command Palette, context menu of the Explorer and Status Bar when a default OpenEdge project is set)_
- **New scratch (run procedure)**
  Creates a new scratch with initial text to `RUN` the selected procedure (only for `*.p` files)
- **Run Scratch**
  Executes the selected scratch in the context of its assigned project
  Default keybinding: `Win+F2` (or `Cmd+F2` for macOS)
  _(Also available via the Command Palette)_
- **Debug Scratch**
  Executes the selected scratch in the context of its assigned project and attaches it to the debugger
  _(Also available via the Command Palette)_
- **Delete Scratch**
  Removes the selected scratch and automatically closes the editor tab if it is currently open
- **Open Scratch**
  Double-click (or right-click) to open the scratch file in the editor
- **Set as description**
  In the context menu of an opened scratch editor, the selected text can be used to set the 'Description' of the scratch

## Screenshot

![Playground](resources/images/playground.gif)

![Playground](resources/images/playground.png)

## Settings

### User / Workspace / Folder
- **Run Mode**
  The run mode when creating a new scratch (`Project setting`, `CHUI`, `GUI` or `Batch`)
  Defaults to `Project setting`
- **Initial Scratch Content**
  The initial text inserted when creating a new scratch
- **Debug Port**
  The debug port for attaching the debugger

### User only
- **Sort Column**
  Sort column in the scratch grid (`Scratch` or `Last run`)
  Defaults to `Scratch`
- **Sort Direction**
  The sort direction of the sort column (`asc` or `desc`)
  Defaults to 'desc'

## Support

### Debugging

#### Debugger
With the Debug action (_button / Command Palette_), a scratch (with modes `gui` and `chui`) can be started with the `debugReady` port. For that, the port number has to be entered in the settings first. Also, set up a launch configuration, example:
```json
 {
   "version": "0.2.0",
   "configurations": [
     {
       "name": "Attach to ABL process",
       "type": "abl",
       "request": "attach",
       "hostname": "localhost",
       "mode": "legacy",
       "port": 3099,
       "pause": true,
       "localRoot": "${workspaceFolder}",
       "refProjects": [ "ProjectA", "ProjectB" ]
     }
   ]
 }
```
Use optional `refProjects` if your project relies on other workspace projects.

When the warning message `11725` (_Use port 3099 for the Debugger to connect to_) appears, the debug launch configuration (`F11`) can be started. The debugger will wait on the first executable line. Click 'Continue' (F5) to go to the first breakpoint.

More info here: [Debugger](https://wiki.rssw.eu/workshop/09-Debugger)

#### Logging
To check debug logging, open the 'ABL Scratch Playground' logging channel in the OUTPUT view and set the log-level to `Debug`

### Issues
Please report issues and feature requests via the GitHub repository.

## Related Extensions
You may also be interested in my other extension: [ABL DataDigger Launcher](https://marketplace.visualstudio.com/items?itemName=vdende.abl-datadigger-launcher).

## Licensing and Legal Notices
- This extension is licensed under the [MIT License](LICENSE).
- OpenEdge and ABL are registered trademarks of Progress Software Corporation.
