---
title: "cintiq button configuration in lucid lynx"
date: 2010-04-30
forum: General Help
---

### Post by lionbeast on 2010-04-30
hello. since i upgraded from karmic to lucid...the script i used to configure my cintiq tablet doesn't seem to work anymore. i searched and found that they replaced wacomtools...but i can't find where they explain how to fix my boutton mapping. i really need your help to map the cintiq shortcut buttons.

---

### Post by Favux on 2010-05-01
Hi lionbeast,

Since there isn't a wacomcpl for xf86-input-wacom yet, wacomcpl's .xinitrc file is missing.  That's the configuration file that contains the xsetwacom commands.

So if you have a backup of .xinitrc just rename it as say .xsetwacom.sh, make it executable, and set it up to autostart.

---

### Post by lionbeast on 2010-05-01
oh ok that sound simple enough...but where can i find a .xinitrc backup.

thanks if this works...than your my savor.

---

### Post by Favux on 2010-05-01
Hi lionbeast,

Well here's part of one by ceridwen on the [Intuos4 thread]("http://ubuntuforums.org/showpost.php?p=7327894&postcount=95").  That's the pad part.  For stylus and eraser here's the relevant part of mine:
```
xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 10 90 100"
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
xsetwacom set eraser bottomy "16630"
xsetwacom set eraser bottomx "26416"
xsetwacom set eraser topy "-101"
xsetwacom set eraser topx "66"
xsetwacom set stylus bottomy "16630"
xsetwacom set stylus bottomx "26416"
xsetwacom set stylus topy "-101"
xsetwacom set stylus topx "66"
```
Clearly your coordinates would be different.  I'd try it like:
```
xsetwacom set stylus Suppress "2"
xsetwacom set stylus RawSample "4"
xsetwacom set stylus ClickForce "6"
xsetwacom set stylus PressCurve "0 10 90 100"
xsetwacom set stylus TPCButton "on"
xsetwacom set stylus Button3 "Button 3"
xsetwacom set stylus Button2 "Button 3"
xsetwacom set stylus Button1 "Button 1"
```
along with the pad stuff.  Xf86-input-wacom should set your coordinates automatically.  The names being used are now longer and more descriptive than stylus, eraser etc.  So 'xinput --list' in a terminal will return something like "Cintiq 6x8" = stylus.  So you'd change the xsetwacom commands like:
```
xsetwacom set stylus PressCurve "0 10 90 100"
```
to
```
xsetwacom set "Cintiq 6x8" PressCurve "0 10 90 100"
```
with the quotes.  Or you can use the ID #.

Hope this helps.

---

### Post by lionbeast on 2010-05-01
thanks i managed to map my bouttons...

setting them up individualy

xsetwacom set "Wacom Cintiq 12WX pad" Button1 "core key a"
xsetwacom set "Wacom Cintiq 12WX pad" Button2 "core key b"
xsetwacom set "Wacom Cintiq 12WX pad" Button3 "core key c"
xsetwacom set "Wacom Cintiq 12WX pad" Button4 "core key d"
xsetwacom set "Wacom Cintiq 12WX pad" Button5 "core key e"
xsetwacom set "Wacom Cintiq 12WX pad" Button6 "core key f"
xsetwacom set "Wacom Cintiq 12WX pad" Button7 "core key g"
xsetwacom set "Wacom Cintiq 12WX pad" Button8 "core key h"
xsetwacom set "Wacom Cintiq 12WX pad" Button9 "core key i"
xsetwacom set "Wacom Cintiq 12WX pad" Button10 "core key j"

etc....

but i don't know how to map the zoom strip on my cintiq. as it's not considered a boutton....i tried

xsetwacom set "Wacom Cintiq 12WX pad" **striplup** "core key k"
xsetwacom set "Wacom Cintiq 12WX pad" **stripldn** "core key k"

because stiplup worked in karmic...but here i suppose it's named diffentely...but i can't figure out how.

---

### Post by Favux on 2010-05-01
Hi lionbeast,

Outstanding work!

Here's another .xinitrc for the Bamboo by shatterblast:  [http://ubuntuforums.org/showpost.php?p=7281908&postcount=188](http://ubuntuforums.org/showpost.php?p=7281908&postcount=188)

The xsetwacom commands are listed at the [LWP's HOWTO]("http://linuxwacom.sourceforge.net/index.php/howto/xsetwacom").

It may be a name problem I suppose.  With that said the xsetwacom commands were rebuilt for xf86-input-wacom so I'm not sure if strip zoom functionality is in there or not.  Try entering in a terminal "xsetwacom list mod" and see what the output is.  Entering 'xsetwacom' alone will give you it's command line options.  You could also check "man wacom" and see what it says.

---

### Post by lionbeast on 2010-05-01
in terminal when i put 
xsetwacom list mod 
i get
unknown argument to list.


so i put xsetwacom list param

and i get

StripLUp         - X11 event to which left strip up should be mapped. 
StripLDn         - X11 event to which left strip down should be mapped. 
StripRUp         - X11 event to which right strip up should be mapped. 
StripRDn         - X11 event to which right strip down should be mapped. 

so i try 

"Wacom Cintiq 12WX pad" StripLUp "core key a"
"Wacom Cintiq 12WX pad" StripLDn "core key b"

but nothing changes.

---

### Post by Favux on 2010-05-01
It sure seems like you are doing that correctly.  So maybe the new xsetwacom commands for xf86-input-wacom don't support strips yet?

Ok, I checked the [xf86-input-wacom git repository]("http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/xf86-input-wacom;a=shortlog").  I think Lucid is using 0.10.5 right now.  There were some button mapping patches added after it came out that should be in 0.10.6 which came out last week.  I can't tell if they affect the strip.

I'd wait a few days to see if you or someone comes up with a solution.  I'll keep my eyes open.  If not then post on LWP's linuxwacom-discuss and ask for help.

---

### Post by lionbeast on 2010-05-01
i asked per email to linuxwacom discuss...but my email has been rejected...

---

### Post by Favux on 2010-05-01
Hi lionbeast,

Good try.  Did you register?  See [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss).  It looks like it's not just you.  I found this post on linuxwacom-discuss from 10 days ago "[xf86-input-wacom touch strips]("https://sourceforge.net/mailarchive/forum.php?thread_name=20100421225753.GA1162%40barra&forum_name=linuxwacom-discuss")".  It looks like the same problem.  Peter Hutterer, who responded, is the lead developer on xf86-input-wacom.  So the top guy knows about the problem.  Because of other priorities it may take him a while to get to it, which is why he asked for help on it.

---

### Post by lionbeast on 2010-05-01
ok...well all i can do is wait....or reinstall karmic....i hate when something works perfectly fine and then it gets broken. 

well thanks for your help.

oh yes i subscribed to the mailing list now....hope that they respond soon.

---

