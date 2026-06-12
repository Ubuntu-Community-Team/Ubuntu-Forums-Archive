---
title: "Missing login dialogue"
date: 2010-09-07
forum: General Help
---

### Post by gmport on 2010-09-07
I am using Ubuntu 10.04 on a HP6730s laptop and frequently have a problem when trying to login. The login splash screen appears, but the login dialogue is missing or flashes up for a fraction of a second then disappears. After pressing the Escape, Return, Ctrl or Alt keys randomly (it doesn't seem to react to any particular key press) eventually the dialogue usually pops up!
 

 Does anyone know what I can do to put this right?


Regards to all
gmport

---

### Post by quixote on 2010-09-10
I don't have an answer, but I'm curious: what happens if you don't press any keys?  Does the dialog eventually come up anyway?  Maybe what you're doing by pressing keys is just filling time, and what makes the login dialog take so long is some minor incompatibility with the graphics card.  It's looking for something, for instance, and has to time out before it will continue.

---

### Post by gmport on 2010-09-23
[SIZE=2] [SIZE=2]Thank you for the reply quixote.[/SIZE]
 
 [SIZE=2]You could well be right with the “filling time” theory. I will try waiting to see if it appears after a period of time when it happens next  (about 1 boot in every 5 or 6). The dialogue does usually flash onto the screen  for a fraction of a second then disappears.[/SIZE]
 
 [SIZE=2]I have found that by moving the mouse cursor to the area  of the screen where the login dialogue should be, left-clicking, then pressing  the space bar or sometimes the Esc key, the login appears. It seems to be hidden  behind the splash screen (if that is possible?).[/SIZE]
 
 [SIZE=2]I have tried changing the splash for another image, but  the problem persists. If the login is in deed being hidden behind the splash  image, is it possible to have no splash image at all, just a blank screen that  will hopefully not allow the login to  show?[/SIZE]

[SIZE=2]Regards[/SIZE]
[SIZE=2]gmport
[/SIZE]
[/SIZE]

---

### Post by quixote on 2010-09-23
To stop the splash screen from displaying takes a small change to /etc/default/grub.  Change this line```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to this```
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
```I'll be curious to hear whether that helps.  I think that just turns off the splash screen, but I've never actually used it myself.  

If it all goes pear-shaped and you wind up losing your graphical login, then you can reinsert the word "splash" on that line after booting into recovery mode.  Just type ```
sudo nano /etc/default/grub
```at the prompt.  (Or without the "sudo" if the prompt looks like "#".  If it does, you're already root, so be very careful what commands you issue.) Ctrl-x will save, and a return will save it under the same name.  Then type "reboot" (without quotes) to restart.

---

### Post by gmport on 2010-09-24
Thanks for that I will try it, but not just yet. I'm working on some end of year accounts and don't want too many complications just at the moment.

I will let you know what happens.

Regards
gmport

---

### Post by gmport on 2010-09-26
quixote,

I tried what you suggested and removed the word 'splash' from the line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

The laptop booted ok... but the problem persists! I'll probably have to live with it as it's more an irritation than a major problem. If you have any further suggestions I would be very interested to hear them. Otherwise thank you for your help.

Regards
gmport.

---

### Post by quixote on 2010-09-26
Well, you could try also removing the word "quiet" on that same line.  Then you'll get screens' worth of text scrolling by, telling you exactly what the boot process is doing, and ultimately the login.  But I doubt that'll help.  The problem sounds like one of those weird glitches that's outside of normal and won't be fixed by anything normal.  Probably, the thing to do is to reinstall whatever program handles login, but I'm not even sure exactly what that is.  Gdm?  But that's the whole gnome desktop manager.  Login-greeter-ui, or whatever it is, is not a standalone package.  If you want to change it, you need "glade," I believe, which has a truly intimidating number of dependencies.  As you say, just living with it may be the simplest solution!

---

### Post by RJ12 on 2010-09-26
Don't forget after changing the GRUB config file to do

```
sudo update-grub
```

I think that actually applies it, but I could be wrong

---

### Post by gmport on 2010-09-29
Thank you **quixote**, I tried to remove "quiet" but it made no difference.... and  thank you **RJ12**, I had remembered to "update-grub".

But then the penny  dropped... it's not the grub splash screen that needs changing, but the  login background. So, I followed the instructions at:

**[http://n00bsonubuntu.com/content/how-change-login-screen-ubuntu-1004-lucid-lynx](http://n00bsonubuntu.com/content/how-change-login-screen-ubuntu-1004-lucid-lynx)**

and selected a plain background.

It's to soon to know if it's done the trick, but I'll let you know.

Regards
gmport

---

### Post by quixote on 2010-09-30
The login background on maverick is something I was just fighting with.  (I hated that orange blobs on purple phase they went through.  The default is less bad now.)  The link you have should work, I think.  It looks a bit more complicated than others I've seen, but that's not necessarily a bad thing.

I did find what seemed to me to be a very simple method.  You don't get much choice, unless you've already downloaded and installed themes you want, but at least you can change the boot / login screens when the devs come up with something truly hideous.  It's from [this forum thread]("http://ubuntuforums.org/showthread.php?p=9795001").> [http://ubuntuforums.org/showthread.php?p=9795001](http://ubuntuforums.org/showthread.php?p=9795001)
1.) Log out, so you are at the GDM (=login) screen.
2.) Press Ctrl-Alt-F1 to change to a virtual terminal.
3.) Log in.
    then run:
```
DISPLAY=:0.0 sudo -u gdm gnome-appearance-properties
```
4.) Go back to the GDM screen: Ctrl-Alt-F8. 
5.) You should see the Appearance Preferences window where you can change everything to your liking.
6.) When you're done, close it and that's it.


---

