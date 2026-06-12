---
title: "Xmonad dzen bar not appearing"
date: 2011-10-29
forum: General Help
---

### Post by Jabrick on 2011-10-29
Ok I've been surfing the forums to try to get a dzen bar to appear.
I've been looking into 
[https://bbs.archlinux.org/viewtopic.php?id=55673](https://bbs.archlinux.org/viewtopic.php?id=55673)

I tried copying his script with corrections.
Currently I don't understand the configurations.
Right now I would just like the bar to appear so I can play around my with configurations and learn how it all works.
With no output I'm not really sure how to learn and debug.

EDIT:
Ok I've finally got a dzen bar to appear.
In my xinitrc where i normally start xmonad
I now have the line

exec xmonad | dzen2

But nothing appears in the bar I've tried several examples and it doesn't seem to work.
Is there something I'm missing?
I do have a ~/.conkyrc file
That looks like
```

# Conky Config File
#
# just log everything to the desktop
#
###

# Main options (alphabetically)
alignment bl
background yes
default_color 606060
draw_outline no
draw_shades no
double_buffer yes
gap_x 10
gap_y 10
minimum_size 100 100
own_window yes
own_window_type override
own_window_transparent yes
total_run_times 0
update_interval 1
use_xft yes
xftalpha 0.7
xftfont Verdana:size=8

# After TEXT is formatted on screen
TEXT
${tail /var/log/everything.log 20}

```

This is my  xmonad config file right now....
If I could just get this to work I can finally tinker around.
Been frustrating! Urgh!

```


--Imports--
import XMonad

--Actions--
import XMonad.Actions.CycleWindows -- classic alt-tab
import XMonad.Actions.CycleWS      -- cycle thru WS', toggle last WS
import XMonad.Actions.DwmPromote   -- swap master like dwm

--Hooks--
import XMonad.Hooks.DynamicLog     -- statusbar 
import XMonad.Hooks.EwmhDesktops   -- fullscreenEventHook fixes chrome fullscreen
import XMonad.Hooks.ManageDocks    -- dock/tray mgmt
import XMonad.Hooks.UrgencyHook    -- window alert bells 
import XMonad.Hooks.SetWMName	   -- matlab fix

--Layouts--
import XMonad.Layout.Named         -- custom layout names
import XMonad.Layout.NoBorders     -- smart borders on solo clients

--Utils--
import XMonad.Util.EZConfig        -- append key/mouse bindings
import XMonad.Util.Run(spawnPipe)  -- spawnPipe and hPutStrLn


import System.IO                   -- hPutStrLn scope


import qualified XMonad.StackSet as W   -- manageHook rules

main = do
        status <- spawnPipe myDzenStatus    -- xmonad status on the left
        conky  <- spawnPipe myDzenConky     -- conky stats on the right
        xmonad $ withUrgencyHook NoUrgencyHook $ defaultConfig
            { modMask            = mod4Mask
            , borderWidth        = 2  
            , normalBorderColor  = "#dddddd"
            , focusedBorderColor = "#0000ff"
--          , handleEventHook    = fullscreenEventHook
            , workspaces = myWorkspaces
            , layoutHook = myLayoutHook
            , manageHook = manageDocks <+> myManageHook
                            <+> manageHook defaultConfig
            ,logHook   = myLogHook status
            , startupHook= setWMName "LG3D"
	    } 
            `additionalKeysP` myKeys

-- Tags/Workspaces
-- clickable workspaces via dzen/xdotool
myWorkspaces            :: [String]
myWorkspaces            = clickable . (map dzenEscape) $ ["1","2","3","4","5"] 
    where clickable l     = [ "^ca(1,xdotool key super+" ++ show (n) ++ ")" ++ ws ++ "^ca()" |
                            (i,ws) <- zip [1..] l,
                            let n = i ]

-- Layouts
-- the default layout is fullscreen with smartborders applied to all
myLayoutHook = avoidStruts $ smartBorders ( full ||| mtiled ||| tiled )
  where
    full    = named "X" $ Full
    mtiled  = named "M" $ Mirror tiled
    tiled   = named "T" $ Tall 1 (5/100) (2/(1+(toRational(sqrt(5)::Double))))
    -- sets default tile as: Tall nmaster (delta) (golden ratio)

-- Window management
--
myManageHook = composeAll
    [ className =? "MPlayer"        --> doFloat
    , className =? "Vlc"            --> doFloat
    , className =? "Gimp"           --> doFloat
    , className =? "XCalc"          --> doFloat
    , className =? "Chromium"       --> doF (W.shift (myWorkspaces !! 1)) -- send to ws 2
    , className =? "Nautilus"       --> doF (W.shift (myWorkspaces !! 2)) -- send to ws 3
    , className =? "Gimp"           --> doF (W.shift (myWorkspaces !! 3)) -- send to ws 4
    , className =? "stalonetray"    --> doIgnore
    ]

-- Statusbar 
--
myLogHook h = dynamicLogWithPP $ myDzenPP { ppOutput = hPutStrLn h }

myDzenStatus = "dzen2 -w '320' -ta 'l'" ++ myDzenStyle
myDzenConky  = "conky -c ~/.conkyrc | dzen2 -x '320' -w '704' -ta 'r'" ++ myDzenStyle
myDzenStyle  = " -h '20' -fg '#777777' -bg '#222222' -fn 'arial:bold:size=11'"

myDzenPP  = dzenPP
   { ppCurrent = dzenColor "#3399ff" "" . wrap " " " "
    , ppHidden  = dzenColor "#dddddd" "" . wrap " " " "
    , ppHiddenNoWindows = dzenColor "#777777" "" . wrap " " " "
    , ppUrgent  = dzenColor "#ff0000" "" . wrap " " " "
    , ppSep     = "     "
    , ppLayout  = dzenColor "#aaaaaa" "" . wrap "^ca(1,xdotool key super+space)· " " ·^ca()"
    , ppTitle   = dzenColor "#ffffff" "" 
                   . wrap "^ca(1,xdotool key super+k)^ca(2,xdotool key super+shift+c)"
                           "                          ^ca()^ca()" . shorten 20 . dzenEscape
    }

-- Key bindings
--
myKeys = [ ("M1-<Tab>"   , cycleRecentWindows [xK_Alt_L] xK_Tab xK_Tab ) -- classic alt-tab behaviour
       	 , ("M-b"	 , sendMessage ToggleStruts	 	 ) -- toggle the status bar gap
         , ("M-<Tab>"    , toggleWS                              ) -- toggle last workspace (super-tab)
         , ("M-<Right>"  , nextWS                                ) -- go to next workspace
         , ("M-<Left>"   , prevWS                                ) -- go to prev workspace
         , ("M-S-<Right>", shiftToNext                           ) -- move client to next workspace
         , ("M-S-<Left>" , shiftToPrev                           ) -- move client to prev workspace
         , ("M-r"        , spawn "xmonad --restart"              ) -- restart xmonad w/o recompiling
         , ("M-x"        , spawn "chromium"                      ) -- launch browser
         , ("M-S-x"      , spawn "chromium --incognito"          ) -- launch private browser
         , ("C-M1-<Delete>" , spawn "sudo shutdown -r now"       ) -- reboot
         , ("C-M1-<End>" , spawn "sudo shutdown -h now"          ) -- poweroff
	 , ("<XF86AudioMute>" , spawn "amixer -q sset Master toggle") --Toggle Volume
	 , ("<XF86AudioLowerVolume>", spawn "amixer -q sset Master 2- unmute") -- lower volume
	 , ("<XF86AudioRaiseVolume>", spawn "amixer -q sset Master 2+ unmute") -- raise volume
	 , ("<Print>"	 , spawn "import -window root `date '+%Y%m%d-%H%M%S'`.png") --Take a Screenshot
         ]

```

---

