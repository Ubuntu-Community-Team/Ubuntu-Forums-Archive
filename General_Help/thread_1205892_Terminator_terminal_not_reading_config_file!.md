---
title: "Terminator terminal not reading config file!"
date: 2009-07-06
forum: General Help
---

### Post by Mercedes300 on 2009-07-06
I have tried uninstalling, re-installing and upgrading! The same config file works on another machine with the same version of terminator! I have now upgraded form 0.12 to 0.13 with no help.

Here is my config file at ~/.config/terminator/config 
```
fullscreen = True
#enable_real_transparency = True
background_darkness = 0.6
titlebars = false


[keybindings]
split_vert = <Ctrl><shift>I

```

I ran it with the verbose option (forget now what it was) and it said it was reading and loading the values from the config file correctly (I will run again and post output if you guys know the option).

Any hints?

Thanks.

---

### Post by Mercedes300 on 2009-07-10
Bump.

Anyone?

---

### Post by Mercedes300 on 2009-10-15
Still having this problem. Anyone have any solutions? Is anyone experancing this too?

Thanks,

Ed.

---

### Post by Mercedes300 on 2009-10-15
OK, did a little more digging (with the help of ZykoticK9 on the ubuntu IRC) got the output of ```
terminator -d
``` as this ```
terminator starting up, version 0.13
profile_cb: settled on profile: "None"
 VS_RCFile: XDG_CONFIG_HOME not found. defaulting to ~/.config
 VS_RCFile: config file located at /home/john/.config/terminator/config
 VS_RCFile: parsing config file
Line 1: '# this is a config file for the terminator terminal emulator.\n'
Skipping: '# this is a config file for the terminator terminal emulator.\n'
Line 2: '\n'
Skipping: '\n'
Line 3: 'fullscreen = True\n'
Setting 'fullscreen'
Value 'True'
Skipping: '\n'
Setting: section=() with 'fullscreen' => 'True'
 VS_RCFile: Set value 'fullscreen' to True
Line 4: '#enable_real_transparency = True\n'
Skipping: '#enable_real_transparency = True\n'
Line 5: 'background_darkness = 0.6\n'
Setting 'background_darkness'
Value '0.6'
Skipping: '\n'
Setting: section=() with 'background_darkness' => '0.6'
 VS_RCFile: Set value 'background_darkness' to 0.59999999999999998
Line 6: 'titlebars = false\n'
Setting 'titlebars'
Value 'false'
Skipping: '\n'
Setting: section=() with 'titlebars' => 'false'
 VS_RCFile: Set value 'titlebars' to False
Line 7: '\n'
Skipping: '\n'
Line 8: '\n'
Skipping: '\n'
Line 9: '[keybindings]\n'
Section 'keybindings'
Skipping: '\n'
Line 10: 'split_vert = <Ctrl><shift>I\n'
Setting 'split_vert'
Value '<Ctrl><shift>I'
Skipping: '\n'
Setting: section=('keybindings',) with 'split_vert' => '<Ctrl><shift>I'
ConfigFile settings are: {'keybindings': {'split_vert': '<Ctrl><shift>I'}, 'fullscreen': True, 'titlebars': False, 'background_darkness': 0.59999999999999998}
 VS_RCFile: setting callback to: <bound method Terminator.reconfigure_vtes of <terminatorlib.terminator.Terminator instance at 0xc61c68>>
VSGConf: Profile bet on is: "None"
VSGConf: Found profiles: "['zipit', 'Monochrome', 'Default', 'full']"
VSGConf: Profile requested is: "None"
 VSGConf: Found profile 'Monochrome' in profile_list
 VSConf: setting callback to: <bound method Terminator.reconfigure_vtes of <terminatorlib.terminator.Terminator instance at 0xc61c68>>
Terminator__init__: comparing None and Monochrome
Using Linux self.pid_get_cwd
Trying to import gnome for X session and backup URL handling support
TConfig: Looking for: 'f11_modifier' in 'RCFile'
Failed to find 'f11_modifier'
TConfig: Looking for: 'f11_modifier' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/f11_modifier
TConfig: Looking for: 'f11_modifier' in 'Default'
Returning 'f11_modifier':'False'
 TConfig: got: 'False' from a 'Default'
Returning 'keybindings':'{'close_window': '<Ctrl><Shift>Q', 'switch_to_tab_10': None, 'resize_left': '<Ctrl><Shift>Left', 'full_screen': 'F11', 'move_tab_left': '<Ctrl><Shift>Page_Up', 'go_right': '<Alt>Right', 'new_tab': '<Ctrl><Shift>T', 'resize_right': '<Ctrl><Shift>Right', 'resize_down': '<Ctrl><Shift>Down', 'toggle_zoom': '<Ctrl><Shift>X', 'scaled_zoom': '<Ctrl><Shift>Z', 'zoom_in': '<Ctrl>plus', 'hide_window': '<Ctrl><Shift><Alt>a', 'move_tab_right': '<Ctrl><Shift>Page_Down', 'prev_tab': '<Ctrl>Page_Up', 'switch_to_tab_6': None, 'switch_to_tab_7': None, 'switch_to_tab_4': None, 'switch_to_tab_5': None, 'split_vert': '<Ctrl><Shift>E', 'switch_to_tab_3': None, 'switch_to_tab_1': None, 'switch_to_tab_2': None, 'group_tab': '<Super>t', 'switch_to_tab_8': None, 'switch_to_tab_9': None, 'zoom_out': '<Ctrl>minus', 'ungroup_all': '<Super><Shift>g', 'go_prev': ('<Ctrl><Shift>P', '<Ctrl><Shift>Tab'), 'close_term': '<Ctrl><Shift>W', 'new_root_tab': '<Ctrl><Shift><Alt>T', 'go_left': '<Alt>Left', 'copy': '<Ctrl><Shift>C', 'paste': '<Ctrl><Shift>V', 'reset': '<Ctrl><Shift>R', 'search': '<Ctrl><Shift>F', 'go_up': '<Alt>Up', 'resize_up': '<Ctrl><Shift>Up', 'next_tab': '<Ctrl>Page_Down', 'split_horiz': '<Ctrl><Shift>O', 'zoom_normal': '<Ctrl>0', 'go_down': '<Alt>Down', 'new_window': '<Ctrl><Shift>I', 'group_all': '<Super>g', 'go_next': ('<Ctrl><Shift>N', '<Ctrl>Tab'), 'ungroup_tab': '<Super><Shift>T', 'reset_clear': '<Ctrl><Shift>G', 'toggle_scrollbar': '<Ctrl><Shift>S'}'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/keybindings
Returning 'keybindings':'{'split_vert': '<Ctrl><shift>I'}'
TConfig: Looking for: 'handle_size' in 'RCFile'
Failed to find 'handle_size'
TConfig: Looking for: 'handle_size' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/handle_size
TConfig: Looking for: 'handle_size' in 'Default'
Returning 'handle_size':'-1'
 TConfig: got: '-1' from a 'Default'
TConfig: Looking for: 'fullscreen' in 'RCFile'
Returning 'fullscreen':'True'
 TConfig: got: 'True' from a 'RCFile'
TConfig: Looking for: 'maximise' in 'RCFile'
Failed to find 'maximise'
TConfig: Looking for: 'maximise' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/maximise
TConfig: Looking for: 'maximise' in 'Default'
Returning 'maximise':'False'
 TConfig: got: 'False' from a 'Default'
TConfig: Looking for: 'borderless' in 'RCFile'
Failed to find 'borderless'
TConfig: Looking for: 'borderless' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/borderless
TConfig: Looking for: 'borderless' in 'Default'
Returning 'borderless':'False'
 TConfig: got: 'False' from a 'Default'
TConfig: Looking for: 'enable_real_transparency' in 'RCFile'
Failed to find 'enable_real_transparency'
TConfig: Looking for: 'enable_real_transparency' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/enable_real_transparency
TConfig: Looking for: 'enable_real_transparency' in 'Default'
Returning 'enable_real_transparency':'False'
 TConfig: got: 'False' from a 'Default'
TConfig: Looking for: 'scrollbar_position' in 'RCFile'
Failed to find 'scrollbar_position'
TConfig: Looking for: 'scrollbar_position' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/scrollbar_position
  GConf: picked function: get_str
 TConfig: got: 'hidden' from a 'GConf'
H9TRANS: composited_support: True
TConfig: Looking for: 'titlebars' in 'RCFile'
Returning 'titlebars':'False'
 TConfig: got: 'False' from a 'RCFile'
TConfig: Looking for: 'titlebars' in 'RCFile'
Returning 'titlebars':'False'
 TConfig: got: 'False' from a 'RCFile'
TConfig: Looking for: 'copy_on_selection' in 'RCFile'
Failed to find 'copy_on_selection'
TConfig: Looking for: 'copy_on_selection' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/copy_on_selection
TConfig: Looking for: 'copy_on_selection' in 'Default'
Returning 'copy_on_selection':'False'
 TConfig: got: 'False' from a 'Default'
TConfig: Looking for: 'exit_action' in 'RCFile'
Failed to find 'exit_action'
TConfig: Looking for: 'exit_action' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/exit_action
  GConf: picked function: get_str
 TConfig: got: 'left' from a 'GConf'
TConfig: Looking for: 'try_posix_regexp' in 'RCFile'
Failed to find 'try_posix_regexp'
TConfig: Looking for: 'try_posix_regexp' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/try_posix_regexp
TConfig: Looking for: 'try_posix_regexp' in 'Default'
Returning 'try_posix_regexp':'False'
 TConfig: got: 'False' from a 'Default'
add_matches: Trying GNU URL regexps.  Set try_posix_regexp = True in config if URLs are not detected.
TConfig: Looking for: 'http_proxy' in 'RCFile'
Failed to find 'http_proxy'
TConfig: Looking for: 'http_proxy' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/http_proxy
TConfig: Looking for: 'http_proxy' in 'Default'
Returning 'http_proxy':''
 TConfig: got: '' from a 'Default'
TConfig: Looking for: 'emulation' in 'RCFile'
Failed to find 'emulation'
TConfig: Looking for: 'emulation' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/emulation
TConfig: Looking for: 'emulation' in 'Default'
Returning 'emulation':'xterm'
 TConfig: got: 'xterm' from a 'Default'
TConfig: Looking for: 'word_chars' in 'RCFile'
Failed to find 'word_chars'
TConfig: Looking for: 'word_chars' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/word_chars
  GConf: picked function: get_str
 TConfig: got: '-A-Za-z0-9,./?%&#:_' from a 'GConf'
TConfig: Looking for: 'mouse_autohide' in 'RCFile'
Failed to find 'mouse_autohide'
TConfig: Looking for: 'mouse_autohide' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/mouse_autohide
TConfig: Looking for: 'mouse_autohide' in 'Default'
Returning 'mouse_autohide':'True'
 TConfig: got: 'True' from a 'Default'
TConfig: Looking for: 'backspace_binding' in 'RCFile'
Failed to find 'backspace_binding'
TConfig: Looking for: 'backspace_binding' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/backspace_binding
  GConf: picked function: get_str
 TConfig: got: 'ascii-del' from a 'GConf'
TConfig: Looking for: 'delete_binding' in 'RCFile'
Failed to find 'delete_binding'
TConfig: Looking for: 'delete_binding' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/delete_binding
  GConf: picked function: get_str
 TConfig: got: 'escape-sequence' from a 'GConf'
TConfig: Looking for: 'font' in 'RCFile'
Failed to find 'font'
TConfig: Looking for: 'font' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/font
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/use_system_font
  GConf: picked function: get_bool
  GConf: picked function: get_str
 TConfig: got: 'monospace 12' from a 'GConf'
TConfig: Looking for: 'allow_bold' in 'RCFile'
Failed to find 'allow_bold'
TConfig: Looking for: 'allow_bold' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/allow_bold
  GConf: picked function: get_bool
 TConfig: got: 'True' from a 'GConf'
TConfig: Looking for: 'palette' in 'RCFile'
Failed to find 'palette'
TConfig: Looking for: 'palette' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/palette
  GConf: picked function: get_str
 TConfig: got: '#2E2E34343636:#CCCC00000000:#4E4E9A9A0606:#C4C4A0A00000:#34346565A4A4:#757550507B7B:#060698209A9A:#D3D3D7D7CFCF:#555557575353:#EFEF29292929:#8A8AE2E23434:#FCFCE9E94F4F:#72729F9FCFCF:#ADAD7F7FA8A8:#3434E2E2E2E2:#EEEEEEEEECEC' from a 'GConf'
TConfig: Looking for: 'use_theme_colors' in 'RCFile'
Failed to find 'use_theme_colors'
TConfig: Looking for: 'use_theme_colors' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/use_theme_colors
  GConf: picked function: get_bool
 TConfig: got: 'False' from a 'GConf'
TConfig: Looking for: 'foreground_color' in 'RCFile'
Failed to find 'foreground_color'
TConfig: Looking for: 'foreground_color' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/foreground_color
  GConf: picked function: get_str
 TConfig: got: '#AAAAAA' from a 'GConf'
TConfig: Looking for: 'background_color' in 'RCFile'
Failed to find 'background_color'
TConfig: Looking for: 'background_color' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/background_color
  GConf: picked function: get_str
 TConfig: got: '#000000' from a 'GConf'
TConfig: Looking for: 'cursor_color' in 'RCFile'
Failed to find 'cursor_color'
TConfig: Looking for: 'cursor_color' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/cursor_color
TConfig: Looking for: 'cursor_color' in 'Default'
Returning 'cursor_color':''
 TConfig: got: '' from a 'Default'
TConfig: Looking for: 'background_type' in 'RCFile'
Failed to find 'background_type'
TConfig: Looking for: 'background_type' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/background_type
  GConf: picked function: get_str
 TConfig: got: 'solid' from a 'GConf'
H9TRANS: Configuring background type as: solid
H9TRANS: Unsetting background image
H9TRANS: Unsetting background image scrolling
H9TRANS: Set background saturation to: 1
H9TRANS: Set opacity to: 65535
TConfig: Looking for: 'cursor_blink' in 'RCFile'
Failed to find 'cursor_blink'
TConfig: Looking for: 'cursor_blink' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/cursor_blink
TConfig: Looking for: 'cursor_blink' in 'Default'
Returning 'cursor_blink':'True'
 TConfig: got: 'True' from a 'Default'
TConfig: Looking for: 'force_no_bell' in 'RCFile'
Failed to find 'force_no_bell'
TConfig: Looking for: 'force_no_bell' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/force_no_bell
TConfig: Looking for: 'force_no_bell' in 'Default'
Returning 'force_no_bell':'False'
 TConfig: got: 'False' from a 'Default'
TConfig: Looking for: 'audible_bell' in 'RCFile'
Failed to find 'audible_bell'
TConfig: Looking for: 'audible_bell' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/audible_bell
TConfig: Looking for: 'audible_bell' in 'Default'
Returning 'audible_bell':'False'
 TConfig: got: 'False' from a 'Default'
TConfig: Looking for: 'visible_bell' in 'RCFile'
Failed to find 'visible_bell'
TConfig: Looking for: 'visible_bell' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/visible_bell
TConfig: Looking for: 'visible_bell' in 'Default'
Returning 'visible_bell':'True'
 TConfig: got: 'True' from a 'Default'
TConfig: Looking for: 'urgent_bell' in 'RCFile'
Failed to find 'urgent_bell'
TConfig: Looking for: 'urgent_bell' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/urgent_bell
TConfig: Looking for: 'urgent_bell' in 'Default'
Returning 'urgent_bell':'False'
 TConfig: got: 'False' from a 'Default'
TConfig: Looking for: 'scrollback_lines' in 'RCFile'
Failed to find 'scrollback_lines'
TConfig: Looking for: 'scrollback_lines' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/scrollback_lines
  GConf: picked function: get_int
 TConfig: got: '2000' from a 'GConf'
TConfig: Looking for: 'scroll_on_keystroke' in 'RCFile'
Failed to find 'scroll_on_keystroke'
TConfig: Looking for: 'scroll_on_keystroke' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/scroll_on_keystroke
  GConf: picked function: get_bool
 TConfig: got: 'True' from a 'GConf'
TConfig: Looking for: 'scroll_on_output' in 'RCFile'
Failed to find 'scroll_on_output'
TConfig: Looking for: 'scroll_on_output' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/scroll_on_output
  GConf: picked function: get_bool
 TConfig: got: 'False' from a 'GConf'
TConfig: Looking for: 'scrollbar_position' in 'RCFile'
Failed to find 'scrollbar_position'
TConfig: Looking for: 'scrollbar_position' in 'GConf'
 VSGConf: returning cached value: hidden
 TConfig: got: 'hidden' from a 'GConf'
TConfig: Looking for: 'focus' in 'RCFile'
Failed to find 'focus'
TConfig: Looking for: 'focus' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/focus
  GConf: picked function: get_str
 TConfig: got: 'click' from a 'GConf'
TConfig: Looking for: 'update_records' in 'RCFile'
Failed to find 'update_records'
TConfig: Looking for: 'update_records' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/update_records
  GConf: picked function: get_bool
 TConfig: got: 'True' from a 'GConf'
TConfig: Looking for: 'login_shell' in 'RCFile'
Failed to find 'login_shell'
TConfig: Looking for: 'login_shell' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/login_shell
  GConf: picked function: get_bool
 TConfig: got: 'False' from a 'GConf'
TConfig: Looking for: 'use_custom_command' in 'RCFile'
Failed to find 'use_custom_command'
TConfig: Looking for: 'use_custom_command' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/use_custom_command
  GConf: picked function: get_bool
 TConfig: got: 'False' from a 'GConf'
TConfig: Looking for: 'login_shell' in 'RCFile'
Failed to find 'login_shell'
TConfig: Looking for: 'login_shell' in 'GConf'
 VSGConf: returning cached value: False
 TConfig: got: 'False' from a 'GConf'
TConfig: Looking for: 'titletips' in 'RCFile'
Failed to find 'titletips'
TConfig: Looking for: 'titletips' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/titletips
TConfig: Looking for: 'titletips' in 'Default'
Returning 'titletips':'False'
 TConfig: got: 'False' from a 'Default'
Saving session for xsm
Session restart command: /usr/bin/terminator with args ['/usr/bin/terminator', '--geometry=642x410+0+0', '-d'] in /home/john
TConfig: Looking for: 'hidden' in 'RCFile'
Failed to find 'hidden'
TConfig: Looking for: 'hidden' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/hidden
TConfig: Looking for: 'hidden' in 'Default'
Returning 'hidden':'False'
 TConfig: got: 'False' from a 'Default'
window state changed: fullscreen: True, maximised: False
window state changed: fullscreen: True, maximised: False
window state changed: fullscreen: False, maximised: False
TConfig: Looking for: 'titletips' in 'RCFile'
Failed to find 'titletips'
TConfig: Looking for: 'titletips' in 'GConf'
 VSGConf: preparing: /apps/gnome-terminal/profiles/Monochrome/titletips
TConfig: Looking for: 'titletips' in 'Default'
Returning 'titletips':'False'
 TConfig: got: 'False' from a 'Default'
```

Here is my config file at ~/.config/terminator/config
```
# this is a config file for the terminator terminal emulator.

fullscreen = True
#enable_real_transparency = True
background_darkness = 0.6
titlebars = false


[keybindings]
split_vert = <Ctrl><shift>I
```

see what the guru's think...

Thanks,

Ed.

---

