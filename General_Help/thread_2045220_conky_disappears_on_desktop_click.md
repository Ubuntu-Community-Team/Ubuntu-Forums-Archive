---
title: "conky disappears on desktop click"
date: 2012-08-20
forum: General Help
---

### Post by pco052 on 2012-08-20
I have the ff. conky script I copied and pasted from some tutorial: [http://pastebin.com/ns77EtEy](http://pastebin.com/ns77EtEy)

It's quite lengthy, but the relevant parts are:

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_type desktop

```

If it is: **own_window_type desktop**
It produces a conky but when i click on the desktop it disappears.

If it is: **own_window_type normal**
Nothing appears

If it is: **own_window_type override**
Nothing appears

Kindly help please, I've been stuck here reading conky threads all afternoon.

---

### Post by pco052 on 2012-08-20
for anyone having a similar problem the solution is:

own_window_type conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

---

### Post by agklimit on 2012-09-16
> **pco052 said:**
> 
If it is: **own_window_type override**
Nothing appears

Strange, bcs "override" does the job for me.

---

### Post by werewolves on 2012-10-28
> **pco052 said:**
> for anyone having a similar problem the solution is:

own_window_type conky
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

Bless you, that was driving me mad!

---

### Post by Sector11 on 2012-10-28
Check these from [http://conky.sourceforge.net/config_settings.html](http://conky.sourceforge.net/config_settings.html)

> **own_window *yes|no***

 	Boolean, create own window to draw? 

own_window_class

 	Manually set the WM_CLASS name. Defaults to "Conky".

own_window_colour

 	If own_window_transparent no, set a specified background colour (defaults to black). Takes either a hex value (e.g. ffffff, note the lack of '#') or a valid RGB name (see /usr/lib/X11/rgb.txt)

own_window_hints

 	If own_window is yes, you may use these window manager hints to affect the way Conky displays. Notes: Use own_window_type desktop as another way to implement many of these hints implicitly. If you use own_window_type override, window manager hints have no meaning and are ignored.

own_window_title

 	Manually set the window name. Defaults to "<hostname> - conky".

own_window_argb_visual 	Boolean, use ARGB visual? ARGB can be used for real transparency, note that a composite manager is required for real transparency. This option will not work as desired (in most cases) in conjunction with 'own_window_type override'.

own_window_argb_value

 	When ARGB visuals are enabled, this use this to modify the alpha value used. Valid range is 0-255, where 0 is 0% opacity, and 255 is 100% opacity.

own_window_transparent

 	Boolean, set transparency? If ARGB visual is enabled, sets background opacity to 0%.

[I]own_window_type

 	**if own_window is yes**, you may specify type normal, desktop, dock, panel or override (default: normal). Desktop windows are special windows that have no window decorations; are always visible on your desktop; do not appear in your pager or taskbar; and are sticky across all workspaces. Panel windows reserve space along a desktop edge, just like panels and taskbars, preventing maximized windows from overlapping them. The edge is chosen based on the alignment option. Override windows are not under the control of the window manager. Hints are ignored. This type of window can be useful for certain situations.[/I] 

---

