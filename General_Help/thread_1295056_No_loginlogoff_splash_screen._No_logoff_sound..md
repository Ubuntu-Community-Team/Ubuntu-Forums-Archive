---
title: "No login/logoff splash screen. No logoff sound."
date: 2009-10-19
forum: General Help
---

### Post by iTheBadGuy on 2009-10-19
I know this has been posted somewhere else, but the solutions they've given hasn't helped me.. so here i go..

I downloaded my ubuntu from the home page - [http://www.ubuntu.com](http://www.ubuntu.com). So i'm positive it's the right image. After my first installation i noticed it didn't have a splash screen but i didn't mind it either.. I installed Kubuntu 9.04 used it for like 3 hours after i decided to go back to Ubuntu, although i like KDE programs, i'm not much of a fan of Kubuntu's interface, it somewhat looks like what i've been trying to get away from - Windows (vista/7).

In Kubuntu it had a splash screen, or atleast it didn't show a black screen for 10 seconds before showing my desktop. And it did have a nice logoff sound to it.. I re-installed my Ubuntu thinking "well, something might of gone wrong throughout the last installation, let me make sure i pay attention this time." So i did.. and everything went fine.. 

*I don't know if this matters, but after the installation was complete and it asked me to remove the CD and then press enter to continue, it showed me many errors.. i wasn't able to copy anything because it was in the bios and it passed by really quick. This happend last installation too. It also showed me these errors with the Kubuntu installation, but it had logoff sound and its splash screen.*

Now sorry for the long post, but i would really like to hear a logoff sound instead of my PC going *BEEEEPP!* - it's annoying. And i would like to see my PC say "Welcome" or something, instead of showing a black screen for 10 seconds..

P.S i tryed ```
sudo apt-get --reinstall install usplash
sudo apt-get --reinstall install libusplash0
sudo apt-get --reinstall install usplash-theme-ubuntu
``` but that didn't seem to help.

Again, sorry for the long post, hope someone can help me fix this, thanks.

---

### Post by iTheBadGuy on 2009-10-19
*Bump*

Not that not having a splash screen/Welcome screen is a problem, or not having a logoff sound. But i like to be able to show my friends Ubuntu from start to finish, i can't do that if something isn't right..

---

### Post by iTheBadGuy on 2009-10-19
*Bump* - 2 Hours latter.. :'(

---

### Post by iTheBadGuy on 2009-10-19
*Bump* - 9 Hours latter...

---

### Post by P4man on 2009-10-19
FWIW, I regularly check the forum tools > unanswered posts for posts that did not receive a reply after 12 or so hours (and i assume im not the only one). bumping your posts actually ensures its no longer in that view as it has received "replies" (or rather bumps)

As for your question; it could be a resolution or color depth problem. can you tell if the screen's backlight is on (despite being black) ? If its off, then the monitor is not displaying the splash. You could try installing *startupmanager* and experiment with different resolutions/color depths.

Other things to try is do an update.

---

### Post by iTheBadGuy on 2009-10-19
Oh ok, i didn't know about the bumping, sorry :P.

But the monitors backlight is on, it shows the cursor but nothing else. i'll try messing with the startupmanager.. i'll let you know how it goes..

---

### Post by iTheBadGuy on 2009-10-19
I messed around with the Startupmanager.. got it, thanks. But i still have no Logoff sound, all i hear is the system beep, is there is a fix?

---

### Post by P4man on 2009-10-19
I dont remember there is one. I suppose you can configure it in preferences > sound. cant be more precise as im on Karmic here.

To get rid of the system speaker beeping, open a terminal and type

```
gksu gedit /etc/modprobe.d/blacklist.conf
```
add this line: ```
blacklist pcspkr
```

---

### Post by iTheBadGuy on 2009-10-19
ah, i see the sound for the Logoff in System -> Preferences -> Sound. I play it and it makes the sound. But it just doesn't play when i logoff.. Anyway thanks for letting me know how to disable the beeping sound.

In some cases something is better than nothing.. in this case, Nothing is better than something :P

Thanks.

---

