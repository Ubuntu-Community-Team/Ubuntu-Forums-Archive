---
title: "Xmonad+Gnome and Desktop Cycling"
date: 2011-05-12
forum: General Help
---

### Post by JHSaunders on 2011-05-12
I am trying to get an Xmonad+Gnome session working on Ubuntu 11.04. I want to have the same key bindings as gnome for moving between desktops (Ctrl+Alt+Left, Ctrl+Alt+Right). I have found XMonad.Actions.CycleWS which should do what I want but for some reason it is not working. When I hit the required key combination nothing happens (at all). I know the key binding is find because I attached a different function to and checked that it was called. Does anyone know what is wrong? My config is below.

```

import XMonad
import XMonad.Config.Gnome

import System.Exit
 
import qualified XMonad.StackSet as W
import qualified Data.Map        as M
import XMonad.Util.EZConfig (additionalKeysP)
import XMonad.Actions.CycleWS 
 
-- Declare config preferences
config_terminal = "gnome-terminal" -- Default terminal to run
config_focusFollowsMouse :: Bool    -- Have focus not follow mouse
config_focusFollowsMouse = True
 
-- Run xmonad with the specified conifguration
main = xmonad $ gnomeConfig {
    terminal            = config_terminal,
    focusFollowsMouse   = config_focusFollowsMouse,
    modMask = mod4Mask
} `additionalKeysP`[ 
  ("M-<F2>", gnomeRun),
  ("M1-<F2>", gnomeRun),
  ("M-<F4>", kill),
  ("M1-<F4>", kill),
  ("M-<U>", windows W.focusUp),
  ("M-<D>", windows W.focusDown),
  ("M-S-<U>", windows W.swapUp),
  ("M-S-<D>", windows W.swapDown),
  ("M1-C-<L>)", prevWS),
  ("M1-C-<R>)", nextWS)
  ]

```

---

