---
title: "Keys won't bind when running fluxbox on xubuntu"
date: 2011-02-27
forum: General Help
---

### Post by DavidIv on 2011-02-27
Hi i'm running fluxbox on my xubuntu 10.10. I'm just trying to set up the key file and the keys i enter will randomly not bind. Like for example:

[I]# open a terminal
Mod1 F1 :Exec x-terminal-emulator

# open a dialog to run programs
Mod1 F2 :Exec fbrun

# filhanterare
Mod1 F3 :Exec thunar

# textredigerare
Mod1 F4 :Exec notepad[/I]

terminal, fbrun and notepad works fine but not thunar. i've tried a million different combos of keys and modifiers and it seems totally random weather it works or not. sometimes what works one minute don't after next reconfigure. 

When i run the original keys-file i get this log output:

*Keys: Invalid key/modifier on line 66): *

I get similar outputs when i change the keys-file for other numbers too but it doesn't seem to happen for every key that doesn't work.

What is going on?

---

### Post by DavidIv on 2011-02-28
the log tells me:
Keys: Invalid key/modifier on line 81):   

this is what my keys-file looks like:

   1.
      ! fluxbox-update_configs added '(workspace=[current])' to (Next|Prev)(Window|Group)
   2.
      ! check lines marked by 'FBCV13' if they are correctly updated
   3.
      !mouse actions added by fluxbox-update_configs
   4.
      OnTitlebar Mouse1 :MacroCmd {Focus} {Raise} {ActivateTab}
   5.
      !mouse actions added by fluxbox-update_configs
   6.
      OnTitlebar Move1 :StartMoving
   7.
      OnLeftGrip Move1 :StartResizing bottomleft
   8.
      OnRightGrip Move1 :StartResizing bottomright
   9.
      OnWindowBorder Move1 :StartMoving
  10.
       
  11.
      # click on the desktop to get menus
  12.
      OnDesktop Mouse1 :HideMenus
  13.
      OnDesktop Mouse2 :WorkspaceMenu
  14.
      OnDesktop Mouse3 :RootMenu
  15.
       
  16.
      # scroll on the desktop to change workspaces
  17.
      OnDesktop Mouse4 :PrevWorkspace
  18.
      OnDesktop Mouse5 :NextWorkspace
  19.
       
  20.
      # scroll on the toolbar to change current window
  21.
      OnToolbar Mouse4 :PrevWindow {static groups} (workspace=[current])  (iconhidden=no) !! FBCV13 !!
  22.
      OnToolbar Mouse5 :NextWindow {static groups} (workspace=[current])  (iconhidden=no) !! FBCV13 !!
  23.
       
  24.
      # Enable dragging of windows via titlebar ( PRT )
  25.
      #OnTitlebar Mouse1 :StartMoving
  26.
       
  27.
      # alt + left/right click to move/resize a window
  28.
      OnWindow Mod1 Mouse1 :MacroCmd {Raise} {Focus} {StartMoving}
  29.
      OnWindow Mod1 Mouse3 :MacroCmd {Raise} {Focus} {StartResizing NearestCorner}
  30.
       
  31.
      # alt + middle click to lower the window
  32.
      OnWindow Mod1 Mouse2 :Lower
  33.
       
  34.
      # control-click a window's titlebar and drag to attach windows
  35.
      OnTitlebar Control Mouse1 :StartTabbing
  36.
       
  37.
      # double click on the titlebar to shade
  38.
      OnTitlebar Double Mouse1 :Shade
  39.
       
  40.
      # middle click on the titlebar to lower
  41.
      OnTitlebar Mouse2 :Lower
  42.
       
  43.
      # right click on the titlebar for a menu of options
  44.
      OnTitlebar Mouse3 :WindowMenu
  45.
       
  46.
      # alt-tab
  47.
      Mod1 Tab :NextWindow {groups} (workspace=[current])  !! FBCV13 !!
  48.
      Mod1 Shift Tab :PrevWindow {groups} (workspace=[current])  !! FBCV13 !!
  49.
       
  50.
      # cycle through tabs in the current window
  51.
      Mod4 Tab :NextTab
  52.
      Mod4 Shift Tab :PrevTab
  53.
       
  54.
      # go to a specific tab in the current window
  55.
      Mod4 1 :Tab 1
  56.
      Mod4 2 :Tab 2
  57.
      Mod4 3 :Tab 3
  58.
      Mod4 4 :Tab 4
  59.
      Mod4 5 :Tab 5
  60.
      Mod4 6 :Tab 6
  61.
      Mod4 7 :Tab 7
  62.
      Mod4 8 :Tab 8
  63.
      Mod4 9 :Tab 9
  64.
       
  65.
      # open a terminal
  66.
      None F1 :Exec xfce4-terminal
  67.
      # open a dialog to run programs
  68.
      None F2 :Exec fbrun
  69.
      # filhanterare
  70.
      None F3 :Exec thunar
  71.
      # textredigerare
  72.
      None F4 :Exec notepad
  73.
      #surfa
  74.
      None F5 :Exec chromium-browser
  75.
      #mail
  76.
      None F6 :Exec thunderbird
  77.
      #torrent
  78.
      None F7 :Exec transmisssion
  79.
      #surfa
  80.
      None F8 :Exec firefox
  81.
       
  82.
      # volume settings, using common keycodes
  83.
      # if these don't work, use xev to find out your real keycodes
  84.
      176 :Exec amixer sset Master,0 1+
  85.
      174 :Exec amixer sset Master,0 1-
  86.
      160 :Exec amixer sset Master,0 toggle
  87.
       
  88.
      # current window commands
  89.
      Mod1 F4 :Close
  90.
      Mod1 F5 :Kill
  91.
      Mod1 F9 :Minimize
  92.
      Mod1 F10 :Maximize
  93.
      Mod1 F11 :Fullscreen
  94.
       
  95.
      # open the window menu
  96.
      Mod1 space :WindowMenu
  97.
       
  98.
      # exit fluxbox
  99.
      Control Mod1 Delete :Exit
 100.
       
 101.
      # change to previous/next workspace
 102.
      Control Mod1 Left :PrevWorkspace
 103.
      Control Mod1 Right :NextWorkspace
 104.
       
 105.
      # send the current window to previous/next workspace
 106.
      Mod4 Left :SendToPrevWorkspace
 107.
      Mod4 Right :SendToNextWorkspace
 108.
       
 109.
      # send the current window and follow it to previous/next workspace
 110.
      Control Mod4 Left :TakeToPrevWorkspace
 111.
      Control Mod4 Right :TakeToNextWorkspace
 112.
       
 113.
      # change to a specific workspace
 114.
      Control F1 :Workspace 1
 115.
      Control F2 :Workspace 2
 116.
      Control F3 :Workspace 3
 117.
      Control F4 :Workspace 4
 118.
      Control F5 :Workspace 5
 119.
      Control F6 :Workspace 6
 120.
      Control F7 :Workspace 7
 121.
      Control F8 :Workspace 8
 122.
      Control F9 :Workspace 9
 123.
      Control F10 :Workspace 10
 124.
      Control F11 :Workspace 11
 125.
      Control F12 :Workspace 12
 126.
       
 127.
      # send the current window to a specific workspace
 128.
      Mod4 F1 :SendToWorkspace 1
 129.
      Mod4 F2 :SendToWorkspace 2
 130.
      Mod4 F3 :SendToWorkspace 3
 131.
      Mod4 F4 :SendToWorkspace 4
 132.
      Mod4 F5 :SendToWorkspace 5
 133.
      Mod4 F6 :SendToWorkspace 6
 134.
      Mod4 F7 :SendToWorkspace 7
 135.
      Mod4 F8 :SendToWorkspace 8
 136.
      Mod4 F9 :SendToWorkspace 9
 137.
      Mod4 F10 :SendToWorkspace 10
 138.
      Mod4 F11 :SendToWorkspace 11
 139.
      Mod4 F12 :SendToWorkspace 12
 140.
       
 141.
      # send the current window and change to a specific workspace
 142.
      Control Mod4 F1 :TakeToWorkspace 1
 143.
      Control Mod4 F2 :TakeToWorkspace 2
 144.
      Control Mod4 F3 :TakeToWorkspace 3
 145.
      Control Mod4 F4 :TakeToWorkspace 4
 146.
      Control Mod4 F5 :TakeToWorkspace 5
 147.
      Control Mod4 F6 :TakeToWorkspace 6
 148.
      Control Mod4 F7 :TakeToWorkspace 7
 149.
      Control Mod4 F8 :TakeToWorkspace 8
 150.
      Control Mod4 F9 :TakeToWorkspace 9
 151.
      Control Mod4 F10 :TakeToWorkspace 10
 152.
      Control Mod4 F11 :TakeToWorkspace 11
 153.
      Control Mod4 F12 :TakeToWorkspace 12

---

