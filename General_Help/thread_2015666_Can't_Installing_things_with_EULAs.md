---
title: "Can't Installing things with EULAs"
date: 2012-07-03
forum: General Help
---

### Post by Subcomfreak on 2012-07-03
I can't do it. I can not install any program that requires me to accept any agreement that comes in the form of a pop-up.

For example, I want to install flash plug-in for firefox (one of the few "required" programs in my opinion). It downloads fine and everything. But then A bocks flashes really quickly on the screen. And from that point on it can never finish installing the program.

I've tested other programs, VLC downloads fine. Audacity downloads and installs fine, restrict tools... nope. MS fonts, nope. Flash, nope. 

I even tried it through the terminal and... it said I did not accept the agreement, and thus it can't install.

So yeah, I'm stuck here and would really like some help. I tried searching on the forums and found no answers.

---

### Post by stderr on 2012-07-03
Interesting. I take it you mean a typical GUI window? It sounds like aptitude may be using another rendering library whose installation is corrupted. You really want it to use a normal curses-style CLI display. 

I'd suggest a workaround to try to force it to do so, like this. Just in case, save all your work before proceeding. Switch to another tty with Ctrl + Alt + F1. (You can switch back to your usual GUI environment with Ctrl + Alt + F7). You should see a login prompt. Login, then proceed to install your applications, e.g.

```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by lisati on 2012-07-03
You might need to make sure that the EULA popup has focus, which is often easily done by clicking on it. You should then be able to navigate the options with the Tab key.

---

### Post by Subcomfreak on 2012-07-03
Sorry that I couldn't get back sooner. I'm going to test your suggestion tomorrow afternoon when I am less tired and have time !

lisati, great idea, except for the fact that it flashes on and off too quick to click it. I'll try pressing tab on an install through the software center. 

To tell you the truth though the terminal is superior if you know what you want. That's coming from guy who just came from windows!

---

### Post by andrew.46 on 2012-07-03
As a side comment you might consider staying aware from applications that want you to agree with EULAs, Terms of Service and the like.

---

### Post by Subcomfreak on 2012-07-03
I whole hardly agree with you. However, flash is one of the few programs that I need in order to do my daily functions :lol: I try to stay away from EULAs as much as possible.

Tried running the work around. Except with "sudo apt-get install flashplugin-installer" The player seemed to install correctly, however, the fonts that were required did not. It said that I did not accept the agreement. I never had a choice:p

Should I boot to ubuntu 2d instead of 3d as my desktop? Or would that matter?

---

### Post by dcstar on 2012-07-04
> **Subcomfreak said:**
> I can't do it. I can not install any program that requires me to accept any agreement that comes in the form of a pop-up.

For example, I want to install flash plug-in for firefox (one of the few "required" programs in my opinion). It downloads fine and everything. But then A bocks flashes really quickly on the screen. And from that point on it can never finish installing the program.
........

```
sudo dpkg-reconfigure debconf
```

Select "Gnome".

---

### Post by lolpenguin on 2012-07-04
You need to install them via a command line, as AFAIK the graphical debconf has some bugs so that the EULA does not appear. Also *try* living without them, which as one reason we use GNU/Linux and other free software, i.e. Ubuntu.

---

### Post by Frogs Hair on 2012-07-04
This is the only package I  have installed  with EULA and it has a check box. I use Flash Aid to install Flash in Firefox and haven't noticed a EULA in the terminal.

---

### Post by Subcomfreak on 2012-07-04
I'm going to try your suggestions. Hold tight for an update.

Flash aid failed.

Trying next suggestion.

I actually don't think it is flash itself. It seems to be the damn Microsoft fonts. Microsoft... who else.

EDIT: dcstar's method worked, but I  still can't accept the ula. Meaning that all the options came out in a "grub" pop-out but the ula didn't.

---

### Post by Krytarik on 2012-07-05
Once the 'ttf-mscorefonts-installer' package is marked as "EULA not accepted", you need to 'purge' and reinstall it to get that EULA dialog (again). To purge it, i.e. remove completely:
```
sudo apt-get purge ttf-mscorefonts-installer
```For reinstallation, either use the Terminal and handle the upcoming EULA dialog with the Tab and Enter keys:
```
sudo apt-get install ttf-mscorefonts-installer
```Or do it the way *Frogs Hair* has suggested, via Software Center or Synaptic.

Regards.

---

### Post by Subcomfreak on 2012-07-05
Suggestion worked. Thanks!

Just purge it first.

---

### Post by dcstar on 2012-07-06
> **Krytarik said:**
> Once the 'ttf-mscorefonts-installer' package is marked as "EULA not accepted", you need to 'purge' and reinstall it to get that EULA dialog (again).
.......

Not necessarily, just running:

```
sudo dpkg-reconfigure <package name>
```

will usually bring up the original config stuff that may have been initially missed.

---

### Post by Krytarik on 2012-07-06
> **dcstar said:**
> Not necessarily, just running:

```
sudo dpkg-reconfigure <package name>
```will usually bring up the original config stuff that may have been initially missed.
Not in this case, unfortunately - have tried that once. ;-)

---

### Post by Subcomfreak on 2012-07-06
Only purging worked for me.

---

### Post by dcstar on 2012-07-07
> **Krytarik said:**
> Not in this case, unfortunately - have tried that once. ;-)

It does depend on the package, some of them do a full "reset" on running that command while others do need the purge to completely wipe them out.

It would be a lot simpler if the Deb packaging rules insisted that everything was run again on a reconfigure, but I guess that we all have to put up with the current situation.

---

