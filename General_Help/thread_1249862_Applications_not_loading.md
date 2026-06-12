---
title: "Applications not loading"
date: 2009-08-25
forum: General Help
---

### Post by sh1ss501 on 2009-08-25
I'm trying to get the apps to work, but no luck.. Earlier today I was on firefox and it was working properly. Then I googled something and then it totally froze. Then I pressed the power button and it turned off, then I pressed it again and the computer turned on, but nothing is working now. The applications try to load, but when it says for example "starting firefox" it disappears... how should I troubleshoot this and is there a virus on it or something?

---

### Post by MTGap on 2009-08-25
There isn't a virus, unless someone had direct access to your computer. Why don't you open the System Monitor and see if firefox is already running just not actually open. (Firefox + Linux = Crap) I always get Firefox is already running since it never closes properly and uses a ton of resources.

You could also just try opening it with the terminal by typing in firefox

---

### Post by sh1ss501 on 2009-08-25
Tried that, the terminal is not loading and it disappears when it says "Starting Terminal"

---

### Post by MTGap on 2009-08-26
Hmm do any applications load at all?

---

### Post by sh1ss501 on 2009-08-27
Nope. Nothing at all. The app show the top of the thing, but I cant type anything, or click on anything at all. Then when I force quit it I click on the app agiain and it tries to load and then it disappers. Has anyone else experienced this kind of problem?

---

### Post by jocko on 2009-08-27
> **sh1ss501 said:**
> I'm trying to get the apps to work, but no luck.. Earlier today I was on firefox and it was working properly. Then I googled something and then it totally froze. [COLOR=Red]Then I pressed the power button and it turned off[/COLOR], then I pressed it again and the computer turned on, but nothing is working now. The applications try to load, but when it says for example "starting firefox" it disappears... how should I troubleshoot this and is there a virus on it or something?
Your file system probably got damaged when you turned off the power. Don't do that except as absoulutely last resort if nothing else works.
You need to check the file system for errors.

If you can still switch to a virtual terminal (Ctrl+Alt+F1), run this:
```
sudo touch /forcefsck
sudo reboot
```That will run a file system check during the next boot.

If you can't get a virtual terminal, boot into recovery mode and drop to a root terminal and run the same commands (without sudo).

Of none of that works, boot up from a live cd and run this in a terminal:
```
sudo fsck -fpC 0 /dev/[COLOR=Red]sda1[/COLOR]
```Change [COLOR=Red]sda1[/COLOR] in that command to the partition where you have ubuntu installed, if you have more than one linux partition you should check them all.

And: the next time your entire system freezes, before you turn off the power, try holding down the Alt and SysRq button while slowly pressing R, E, I , S, U, B. That will kill all applications, finish any writes to the file system, remount the file system in read-only mode and then reboot.
Or if it was just some application that is frozen, just kill that application, or close all other applications and restart xorg with the key combination: Alt+SysRq+K

---

