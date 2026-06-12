---
title: "Desktop Won't Come Up"
date: 2009-08-25
forum: General Help
---

### Post by WalkerInTheWoods on 2009-08-25
I recently got a netbook and have been using the Ubuntu Netbook Remix on it. It has been great. I was messing around with it and switched the desktop to the traditional style. While still in that I shut down. 

Later I boot back up but all that will load up is the background image. I get neither desktop to load up. How can I get either one back up?

Thank you.

---

### Post by Anticontrame on 2009-08-25
Odd. Try hitting Alt-F2, typing desktop-switcher, and hitting run.

---

### Post by WalkerInTheWoods on 2009-08-25
Hitting Alt-F2 doesn't do anything.

---

### Post by WalkerInTheWoods on 2009-08-25
Ok, here is what I can do. I can hit ctrl-l and that brings up location. From there I can go to home in nautilus. There I can go to ~/.config/autostart and launch netbook-launcher.desktop, which brings up the netbook desktop. If I go to the desktop switcher it shows that the netbook desktop is selected. If I restart though I still get just the background and nothing else loading up, unless I do the whole process again. Also it does not load up the top bar showing the battery meter, network, etc.

---

### Post by Anticontrame on 2009-08-26
Is Netbook Launcher checked in preferences>Startup Applications?

---

### Post by WalkerInTheWoods on 2009-08-26
I checked the two options that were not checked and now the main "window" (I guess you would call it) for the netbook desktop comes up, but the top panel which shows battery charge, network, etc does not come up.

---

### Post by WalkerInTheWoods on 2009-08-26
The following solved my problem from this thread: [http://ubuntuforums.org/showthread.php?p=7852751#post7852751](http://ubuntuforums.org/showthread.php?p=7852751#post7852751)

> **bodhi.zazen said:**
> I am guessing your configuration files are corrupted.

I have had this happen on a few occasions and to be honest, easiest thing to do iss to move your entire home directory.

Boot to recovery mode , run a root shell

```
mv /home/your_user /home/your_user.bak
mkdir /home/your_user
chown your_user:your_user /home/your_user
```

then exit and at the recovery menu continue booting.

You will loose your configuration for your desktop, but should be easy to fix.

If you need data or other files from your old home, move it from the back up (your_user.bak) to the new home.

Once you are happy your have moved everything you need, you can delete the old (or back it up off your hard drive).

IMO this is easier then attempting to restore corrupt config files.

The one file you might want is /home/your_user_bak/.mozilla 

Good luck.

---

