# modes.nvim

> Prismatic line decorations for the adventurous vim user

Highlight UI elements based on current mode. Inspired by the recent addition of vim bindings in Xcode-beta.

## Usage

```lua
use({
  'mvllow/modes.nvim',
  config = function()
    require('modes').setup()
  end
})
```

![Jul-27-2021 13-19-12](https://user-images.githubusercontent.com/1474821/127207394-0cca49b9-1cb0-4869-9310-9f9a922d3da0.gif)

## Options

> Note: `vim.opt.cursorline` must be set to true for lines to be highlighted

Default colors can be overridden by passing values to the setup function or updating highlight groups (useful for themes).

```lua
-- Pass colors through setup
require('modes').setup({
  colors = {
    copy = "#f5c359",
    delete = "#c75c6a",
    insert = "#78ccc5",
    visual = "#9745be",
  },
  line_opacity = 0.1
})

-- Or use highlight groups (useful for themes)
vim.cmd('hi ModesCopy guibg=#f5c359),
vim.cmd('hi ModesDelete guibg=#c75c6a),
vim.cmd('hi ModesInsert guibg=#78ccc5),
vim.cmd('hi ModesVisual guibg=#9745be),
```

In the future, highlight groups will be customizable. More documentation coming soon!

## Known issues

- Some _Which Key_ presets conflict with this plugin. For example, `d` and `y` operators will not apply highlights if `operators = true` because _Which Key_ takes priority

_Workaround:_

```lua
require('which-key').setup({
  plugins = {
    presets = {
      -- Disable operators
      operators = false,
    },
  },
})
```

- Line highlights are applied to all buffers, not just the active one
- Named colors are not yet supported. For example, `colors.copy = 'blue'` does not work. _Workaround: use complete hex colors_
