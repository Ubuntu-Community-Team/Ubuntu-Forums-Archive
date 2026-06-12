---
title: "Missing window borders/title bars"
date: 2009-09-24
forum: General Help
---

### Post by MegaLoler on 2009-09-24
When I have desktop effects on, the boarders and title bars on windows disappear.  When desktop effects are off, they come back.  Is there a way to fix this without turning off desktop efects?

---

### Post by kingchipo on 2009-09-24
let me get this straight.

When you enable desktop effects your title bar disapears.. ie you cannot close or minimize windows?

---

### Post by tuxxy on 2009-09-24
Once the effects are enabled and the titlebars vanish then press ALT + F2 and enter this command;

```
emerald --replace
```

Your new window bars will appear now to edit them and also change themes you need emerald theme managaer so search for emerald in Synaptic or enter this command in terminal;

```
sudo apt-get install emerald
```

Also it might be a good idea to add emerald to your startup applications to save you having to run through this process again at bootup.

---

### Post by MegaLoler on 2009-09-24
I can, but not with the buttons on the title bar.  I have to use the panel at the bottom and keyboard shortcuts.

---

### Post by MegaLoler on 2009-09-24
> **tuxxy said:**
> Once the effects are enabled and the titlebars vanish then press ALT + F2 and enter this command;

```
emerald --replace
```Your new window bars will appear now to edit them and also change themes you need emerald theme managaer so search for emerald in Synaptic or enter this command in terminal;

```
sudo apt-get install emerald
```Also it might be a good idea to add emerald to your startup applications to save you having to run through this process again at bootup.
   Oh, u posted before me.  Ok i will do that.

---

### Post by kingchipo on 2009-09-24
mega replacing with emerald will work but compiz is crashing when your enabling desktop effects theres most likely a problem with your video card clashing with compiz..

---

### Post by MegaLoler on 2009-09-24
emerald --replace didn't do anything, with alt-2 or with the terminal.  But the terminal window is completely white with desktop effects enabled so I can't see what is said, but it didn't say anything with desktop effects turned off.

---

### Post by etnlIcarus on 2009-09-24
Looks like either compiz hates you or your video driver is lacking.

Without desktop effects enabled, open a terminal and type glxgears.

Do you get a window with 3D gears?

---

### Post by tuxxy on 2009-09-24
Yes you cant run emerald without compiz enabled.  If compiz is giving you errors first then emerald will not be able to run anyway.

---

### Post by MegaLoler on 2009-09-24
glxgears does give me gears.  OpenGl apps work, but some games are incredibly slow.  And besides the window borders, the desktop effects work very well. And fast, too.

---

### Post by tuxxy on 2009-09-24
What video card are you running, maybe it has issues with 3D graphics..I had an ATI card like that

---

### Post by etnlIcarus on 2009-09-24
Could just be that Emerald is an ill-maintained and buggy decorator.

Perhaps try installing fusion-icon and setting your decorator from there.

---

### Post by MegaLoler on 2009-09-24
> **tuxxy said:**
> What video card are you running, maybe it has issues with 3D graphics..I had an ATI card like that

The terminal says:

0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200]
 (rev 01)
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 PCI
0001:10:17.0 Class ff00: Apple Computer Inc. KeyLargo/Intrepid Mac I/O
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB Controller: Apple Computer Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.1 USB Controller: NEC Corporation USB (rev 43)
0001:10:1b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth 2 Internal PCI
0002:20:0d.0 Class ff00: Apple Computer Inc. UniNorth/Intrepid ATA/100
0002:20:0e.0 FireWire (IEEE 1394): Apple Computer Inc. UniNorth 2 FireWire (rev 
81)
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth 2 GMAC (Sun GEM) 
(rev 80)

Oh, and I forgot to mention that I have a g4 Mac Mini (PPC) and I've never had any graphics problems in Mac OS X before.

---

### Post by rossmoore on 2009-09-24
Everyone seems to be concentraing on using emerald. I happen to prefer the shiki colours theme with metacity as the window decorator. You can set this within compiz. To see if metacity will work, try the following:
Hit Alt+F2 and type:
```
metacity --replace
```
Hopefully you'll get your windows and borders back again.

I that works you change the default "window decorator" in compiz, changing it to metacity. I'm not at my ubuntu install right now so I can't quite remember what screen it's on, but a bit of common sense should help you spot it.

Of course this doesn't explain why the window decorator compiz is currenty trying to use is failing... but it does give you windows!

---

### Post by MegaLoler on 2009-09-24
> **rossmoore said:**
> Everyone seems to be concentraing on using emerald. I happen to prefer the shiki colours theme with metacity as the window decorator. You can set this within compiz. To see if metacity will work, try the following:
Hit Alt+F2 and type:
```
metacity --replace
```Hopefully you'll get your windows and borders back again.

I that works you change the default "window decorator" in compiz, changing it to metacity. I'm not at my ubuntu install right now so I can't quite remember what screen it's on, but a bit of common sense should help you spot it.

Of course this doesn't explain why the window decorator compiz is currenty trying to use is failing... but it does give you windows!

I did that, and it disabled desktop effects.  It did bring the windows back but no effects.

---

### Post by etnlIcarus on 2009-09-25
> **etnlIcarus said:**
> Perhaps try installing fusion-icon and setting your decorator from there.

Also make sure you've got compiz-gnome installed.

---

### Post by rossmoore on 2009-09-25
> I did that, and it disabled desktop effects. It did bring the windows back but no effects
That is weird. Sounds like we need to figure out why things aren't working currently then...

---

### Post by MegaLoler on 2009-09-25
> **etnlIcarus said:**
> Also make sure you've got compiz-gnome installed.

I did this, and it didn't work.  If I understand correctly the window manager is the program that draws the window borders?  Then what is the window decorator?

---

### Post by etnlIcarus on 2009-09-25
The window manager is what gives your your functionality. A window decorator is exactly what it sounds like. Traditionally, they would be one in the same but compiz kind of throws that simplicity out the window:

compiz-gnome includes the, "gtk window decorator", which is  fancy way of saying it inherits Metacity's appearance but it's still using compiz for management.

If, using the fusion-icon, you choose the gtk-window-decorator, instead of emerald, and play around with all the other options fusion-icon exposes, and still can't get compiz working properly, we can pretty much rule out this train of thought.

The next thing to try will be to stop compiz, rename the $HOME/.config/compiz directory to $HOME/.config/compiz_bkp, then try starting compiz again.

---

### Post by MugOTea on 2009-09-25
I've got Ubuntu installed on a HP/ Compaq 6720s laptop - everything was fine yesterday, i've logged in today and I too have no titlebars or window borders... I've tried the sugestions on this thread but no luck in fixing it yesterday. Is there a way to check if any of the Ubuntu Update Managers updates have caused this?

I can still use the terminal windows but I think thats more because of the theme settings, the terminal goes full screen and white but fortunately my text colour is black.

It's amazing how much you can miss titlebars for forms on XWin style systems...

---

### Post by MugOTea on 2009-09-25
Oooh - I just fixed my install!!! :D

I'm a bit of a linux noob but as you can see from my last post I was struggling with a similar problem, and tried all the suggestions (ended up with KDE installed too just to try and get mi titlebars back)...

I eventually found that in my start-up programs, an app called "Devilspie" was selected to initialise with the system... apperently its a utility for simplyfing the display to multiple monitors.... I don't remember installing anything like this so I'm not sure where it came from, or if it was just something I clicked as an option somewhere...

Anyway, long-story short, removed that from the startup processes "SYSTEM>Preferences>Startup Applications" and restarted the computer, and now I've got title bars again! :)

:guitar:

---

### Post by MegaLoler on 2009-09-25
> **MugOTea said:**
> Oooh - I just fixed my install!!! :D

I'm a bit of a linux noob but as you can see from my last post I was struggling with a similar problem, and tried all the suggestions (ended up with KDE installed too just to try and get mi titlebars back)...

I eventually found that in my start-up programs, an app called "Devilspie" was selected to initialise with the system... apperently its a utility for simplyfing the display to multiple monitors.... I don't remember installing anything like this so I'm not sure where it came from, or if it was just something I clicked as an option somewhere...

Anyway, long-story short, removed that from the startup processes "SYSTEM>Preferences>Startup Applications" and restarted the computer, and now I've got title bars again! :)

:guitar:

I didn't have an app called Devilspie in my startup applications.  And it's not listed in the processes that are running either.

> **etnlIcarus said:**
> The window manager is what gives your your functionality. A window decorator is exactly what it sounds like. Traditionally, they would be one in the same but compiz kind of throws that simplicity out the window:

compiz-gnome includes the, "gtk window decorator", which is fancy way of saying it inherits Metacity's appearance but it's still using compiz for management.

If, using the fusion-icon, you choose the gtk-window-decorator, instead of emerald, and play around with all the other options fusion-icon exposes, and still can't get compiz working properly, we can pretty much rule out this train of thought.

The next thing to try will be to stop compiz, rename the $HOME/.config/compiz directory to $HOME/.config/compiz_bkp, then try starting compiz again.

I tried this but it didn't make any difference.  Still no borders.

---

### Post by etnlIcarus on 2009-09-25
Try initialising compiz from a terminal and pasting the output here.

---

### Post by CrusaderAD on 2009-10-22
Install and go into CompizConfig Settings Manager. Go to Effects, Windows Decoration. Make sure it's enabled and that

```
/usr/bin/compiz-decorator
```

Is in the command field. This worked for me!

---

### Post by MegaLoler on 2009-10-26
> **raptormanad said:**
> Install and go into CompizConfig Settings Manager. Go to Effects, Windows Decoration. Make sure it's enabled and that

```
/usr/bin/compiz-decorator
```Is in the command field. This worked for me!

I did that, and now it says desktop effects can't be enabled.

---

### Post by stinkeye on 2009-10-26
Having metacity compositing manager enabled would cause me these sorts of problems when switching window managers.
To disable:In gconf-editor
/apps/metacity/general/compositing_manager and untick.
For me, with it disabled the compiz --replace works without error.

---

### Post by MegaLoler on 2009-10-27
> **stinkeye said:**
> Having metacity compositing manager enabled would cause me these sorts of problems when switching window managers.
To disable:In gconf-editor
/apps/metacity/general/compositing_manager and untick.
For me, with it disabled the compiz --replace works without error.

I looked and it is unchecked already.

EDIT: It's fixed!  Upgrading to Karmic fixed the windows!  yay!

---

