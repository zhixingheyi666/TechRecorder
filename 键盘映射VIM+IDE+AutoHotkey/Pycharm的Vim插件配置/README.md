IdeaVim is a Vim emulation plugin for IDEs based on the IntelliJ Platform. IdeaVim can be used with IntelliJ IDEA, PyCharm, CLion, PhpStorm, WebStorm, RubyMine, AppCode, DataGrip, GoLand, Rider, Cursive, and Android Studio.

Resources:

    Plugin homepage
    Changelog
    Bug tracker
    Continuous integration builds
    @IdeaVim in Twitter

Installation

Use the IDE's plugin manager to install the latest version of the plugin. Start the IDE normally and enable the Vim emulation using "Tools | Vim Emulator" menu item. At this point you must use Vim keystrokes in all editors.

If you wish to disable the plugin, select the "Tools | Vim Emulator" menu so it is unchecked. At this point your IDE will work with its regular keyboard shortcuts.

Keyboard shortcut conflicts between the Vim emulation and the IDE can be resolved via "File | Settings | Editor | Vim Emulation", "File | Settings | Keymap" on Linux & Windows, and via "Preferences | Editor | Vim Emulation", "Preferences | Keymap" on macOS. They can also be resolved by key-mapping commands in your ~/.ideavimrc file.
Get Early Access

Would you like to try new features and fixes? Join the Early Access Program and receive EAP builds as updates!

    Click the IdeaVim icon in the status bar | EAP | Get Early Access...

Or subscribe to EAP updates manually:

    Open Settings | Plugins
    Click the gear icon gear, select Manage Plugin Repositories, and add the following url: https://plugins.jetbrains.com/plugins/eap/ideavim

See the changelog for the list of hot unreleased features.

It is important to distinguish EAP builds from traditional pre-release software. Please note that the quality of EAP versions may at times be way below even usual beta standards.

You can always leave your feedback with:

    @IdeaVim in Twitter
    Bug tracker

Summary of Supported Vim Features

Supported:

    Motion keys
    Deletion/changing
    Insert mode commands
    Marks
    Registers
    Undo/redo
    Visual mode commands
    Some Ex commands
    Some :set options
    Full Vim regexps for search and search/replace
    Key mappings
    Macros
    Digraphs
    Command line and search history
    Window commands
    Vim web help
    Select mode

Emulated Vim plugins:

    vim-surround
    vim-multiple-cursors
    vim-commentary

Not supported (yet):

    Jump lists
    Various less-used commands

See also:

    The list of all supported commands
    Top features and bugs

Files

    ~/.ideavimrc
        Your IdeaVim-specific Vim initialization commands

You can read your ~/.vimrc file from ~/.ideavimrc with this command:

source ~/.vimrc

Note, that IdeaVim currently parses ~/.ideavimrc file via simple pattern matching. See VIM-669 for proper parsing of VimL files.

Also note that if you have overridden the user.home JVM option, this will affect where IdeaVim looks for your .ideavimrc file. For example, if you have -Duser.home=/my/alternate/home then IdeaVim will source /my/alternate/home/.ideavimrc instead of ~/.ideavimrc.

Alternatively, you can set up initialization commands using XDG standard. Put your settings to $XDG_CONFIG_HOME$/ideavim/ideavimrc file. [To Be Released]
Emulated Vim Plugins

IdeaVim extensions emulate some plugins of the original Vim. In order to use IdeaVim extensions, you have to enable them via this command in your ~/.ideavimrc:

set <extension-name>

Available extensions:

    easymotion
        Setup:
            Install IdeaVim-EasyMotion and AceJump plugins.
            set easymotion
        Emulates vim-easymotion
        Commands: All commands with the mappings are supported. See the full list of supported commands.

    surround
        Setup: set surround
        Emulates vim-surround
        Commands: ys, cs, ds, S

    multiple-cursors
        Setup: set multiple-cursors
        Emulates vim-multiple-cursors
        Commands: <A-n>, <A-x>, <A-p>, g<A-n>

    commentary
        Setup: set commentary
        Emulates commentary.vim
        Commands: gcc, gc + motion, v_gc

Changes to the IDE
Undo/Redo

The IdeaVim plugin uses the undo/redo functionality of the IntelliJ Platform, so the behavior of the u and <C-R> commands may differ from the original Vim. Vim compatibility of undo/redo may be improved in future releases.

See also unresolved undo issues.
Escape

Using <Esc> in dialog windows remains problematic. For most dialog windows, the Vim emulator is put into insert mode with <Esc> not working. You should use <C-c> or <C-[> instead. In some dialog windows, the normal mode is switched by default. The usage of the Vim emulator in dialog windows is an area for improvement.

See also unresolved escape issues.
Executing IDE Actions

IdeaVim adds two commands for listing and executing arbitrary IDE actions as Ex commands or via :map command mappings:

    :actionlist [pattern]
        Find IDE actions by name or keymap pattern (E.g. :actionlist extract, :actionlist <C-D)
    :action {name}
        Execute an action named NAME

For example, here \r is mapped to the Reformat Code action:

:map \r :action ReformatCode<CR>

Contributing

See CONTRIBUTING.md
Authors

See AUTHORS.md for a list of authors and contributors.
License

IdeaVim is licensed under the terms of the GNU Public License version 2 or any later version.