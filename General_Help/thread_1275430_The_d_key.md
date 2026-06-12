---
title: "The d key"
date: 2009-09-25
forum: General Help
---

### Post by mr_shedges on 2009-09-25
Hello all,

I was trying some new things today and ended up pushing Super+R and could not find out a way to undo it. So I naturally hit all the keys to try and undo. But when I went to the Terminal screen I found that when I type a "d" I get a dialogue box asking me to change the title. so at the moment every time I type "d" in the terminal I get a dialogue box asking me to change the title.

Any help would be great.

Thanks

---

### Post by clonne4crw on 2009-09-25
Unplug the keyboard and plug it back in?

---

### Post by mr_shedges on 2009-09-26
Sounds like a plan, but I have a laptop so I have not option to unplug it. shoudl have said this before.

---

### Post by cholericfun on 2009-09-26
sounds like a job for the recovery option on bootup

not too sure what exactly needs to get fixed though...

maybe some more details what you changed?

---

### Post by 3rdalbum on 2009-09-26
Super-R doesn't do anything here... what was it meant to do and what did it do?

If it's a Compiz keybinding, then go to the Compiz Config Settings Manager and uncheck the box next to the place where you set the keybinding.

---

### Post by Iowan on 2009-09-26
Kinda sounds like a sticky key. System>Preferences>Keyboard>Accessibility has the option to turn on/off accessibility features.

You might also check the Edit>Keyboard Shortcuts in the terminal. 
The "Set Title" shortcut is "Disabled" on my terminal.

---

### Post by mr_shedges on 2009-10-05
OK this is silly, I have one of those bloody acer machines with the toggle switches for blue-tooth and wifi. What a pain in the ****. I must have hit the wifi one by mistake. I have no idea what it does but the out come is the wifi card is enabled but does not work. So the last couple of days I have had to figure out what to do, simple really start up in windows. Enable, Disable then Enable via the switch on the lappy. then it worked. I mean really.

So now back on line on Ubuntu.

So the d key.
Tried all of the above, except unplugging the keyboard. nothing. I had set the terminal to display when I pushed Super L. When testing this I must have hit some weird keys, all of a sudden my screen zoomed in. I later found (after hitting most of the keys + windows key) that it was r.

So Windows + R = zoomed in looks nice. But how to I get out?. So again I started to hit more keys + windows Key. I then found that Windows + E = show all desktops. Pretty.

After the post above I checked the keyboard shortcuts, windows key is not in there at all.

So with no short cut how does this work? and more to the point how do I zoom out????? Reboot sorts it but that is a pain in the ****. and the d key is still causing me pain.

After this happened, the d key now brings a title not the character in the terminal. As I found out when i typed edit or rather e then changed the title.

Not sure if I made it fully clear, but the d only seems to bring the display title in the terminal. but this is the app I was in when I did all of this.:(:P:):confused:

Any Ideas.

I noticed the recovery option mentioned above how do I get that? wqill it work?

Thanks Scott

---

### Post by cholericfun on 2009-10-08
ok
when you boot, choose recovery in the GRUB menu
then try fix x-server

this will kill your screensettings but it might also kill any of your weird key-settings
might...
i thought there was something about keyboard as well, but i just had a quick look and didnt find what i thought would see...

try it out anyway.

---

### Post by mr_shedges on 2009-10-08
So I found possibly the dirtiest fix ever. I installed Konsole and heay presto I have shell again. Seems to only effect Terminal.  Is there a binding folder just for this app?

---

