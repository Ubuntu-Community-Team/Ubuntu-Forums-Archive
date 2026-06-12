---
title: "Clickable dzen bar"
date: 2011-11-01
forum: General Help
---

### Post by Jabrick on 2011-11-01
So I've gotten the dzen bar to appear with xmonad.
I'd now like to make it clickable.
All the samples online seem fairly simple.
But mine isn't working.
The click functionality doesn't work, and instead of named workspaces, it prints out 

^a(1,xdotool key super+1)1^1a()
Where it should show the workspace numbers

I do have xdotool installed.

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

import Data.List
import System.IO                   -- hPutStrLn scope


import qualified XMonad.StackSet as W   -- manageHook rules

main = do
	statuspipe <- spawnPipe "dzen2 -w '320' -ta 'l'" 
        xmonad $ withUrgencyHook NoUrgencyHook $ defaultConfig
            { modMask            = mod4Mask
            , borderWidth        = 2  
            , normalBorderColor  = "#dddddd"
            , focusedBorderColor = "#0000ff"
--          , handleEventHook    = fullscreenEventHook
            , workspaces = myWorkspaces
            , layoutHook = myLayoutHook
	    , manageHook = manageDocks <+> manageHook defaultConfig
	    , startupHook= setWMName "LG3D"
	    ,   logHook = dynamicLogWithPP $ defaultPP 
	 {
	    ppCurrent = dzenColor "#3399ff" "" . wrap " " " "
    	    , ppHidden  = dzenColor "#dddddd" "" . wrap " " " "
    	    , ppHiddenNoWindows = dzenColor "#777777" "" . wrap " " " "
    	    , ppUrgent  = dzenColor "#ff0000" "" . wrap " " " "
    	    , ppSep     = "     "
	    , ppLayout  = dzenColor "#aaaaaa" "" . wrap "^ca(1,xdotool key super+space)· " " ·^ca()"
	    , ppTitle   = dzenColor "#ffffff" "" 
                    . wrap "^ca(1,xdotool key super+k)^ca(2,xdotool key super+shift+c)"
                           "                          ^ca()^ca()" . shorten 20 . dzenEscape
   	 }
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

