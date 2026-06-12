---
title: "Touchpad stopped working Ubuntu 10.10"
date: 2010-11-25
forum: General Help
---

### Post by rambo9 on 2010-11-25
Hello. I have been using Ubuntu 10.10 for about a week now, I have had many, many problems, but usually figure them out by searching through this forum, except this time:
I have an HP touchsmart tx2 1025dx laptop. When I installed it, everything worked great, sound, mouse, and even the touchscreen. Right now I noticed that when I press the button on by laptop which toggles the touchpad, it works but after it would freeze the menus, so that they would not drop down, I have confirmed this after many restarts. Now the touchpad has stopped working completely. Although if use the toggle button, it will still freeze by menus. It also somehow stops my keyboard from typing things into programs, like firefox, but still somehow the control-alt delete still lets me restart it.  My question is how can I reset the mouse settings/preferances to how they were when I installed? I found something a while back that was xorgconfig??? but it has since been taken out of ubuntu 10.10 (I read this somewhere, please correct me if I'm wrong.) I hope this is enough information for someone to point me in the right direction.

Recap:
Laptop Touchpad not working
When I press the toggle Touchpad button, messes up the menus
Using HP Touchsmart Tx2 1025dx Laptop

Looking for a way to reset/restore sound preferences/settings or enable touchpad/

ps: I was able to come here because the touchscreen is still working :-)

I ended up  doing this:
[B]rm -rf .gnome .gnome2 .gconf .gconfd .metacity
[/B]
which reset ALL of my settings back to when I installed it, without deleting my programs or files.
I found this here: [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by Swirlsky on 2010-11-29
I have the same laptop, and the same problem. I've been using Ubuntu on my tx2z for a year by now, and today the touchpad completely stopped working, I have reinstalled Ubuntu 10.10 two times, but nothing changed. Now I have a completey unusable laptop, I have no other operating system, and any other computer. I'm in a really big trouble now...

---

### Post by Swirlsky on 2010-11-30
Some additional information:
The problem also occurs on Linux Mint with HP tx2z. The Cursor keeps jumping to the top-left corner of the screen.
What I figured out:
Running Google Chrome maximized in the background solves the problem. I could not find any other applications that would do the same. I do not know how it can be in connection with Chrome, but this is one more reason I love Chrome so much :))

Btw, I hope someone will provide a fix for this bug, since it seems to be a "Linux-illness", as it obtains not only in Ubuntu.

---

### Post by ithatcher123 on 2010-12-05
I have the same computer and as of this morning I have the same problem. any news on this would be awesome, cause like you guys im just using the touch screen and its getting old.

---

### Post by airjer on 2010-12-10
Same issue here :(

HP TouchSmart tx2-1012nr

---

### Post by marwansherin on 2011-02-10
Hi,
I've just got it working. I was having the same problem too!! and it's too annoying. So here it is
when it is not working just press CTRL + ALT + F4 to go to a different login screen, just go to any different login screen, then come back to the GUI one by pressing CTRL + ALT + F7, and the touch pad is working again, and the keyboard too, that's where I'm typing this now :)

HP TouchSmart tx2-1250ee

---

### Post by hobbbid hobbin on 2011-04-04
I don't have a touch screen computer but if I press the disable touchpad button then enable it again I get the same problem.
CTRL + ALT + F4 just makes my computer screen turn black and stop responding. I ran this command:

gconftool-2 --set --type boolean /desktop/gnome/peripherals/touchpad/touchpad_enabled true

then rebooted my computer. It worked hence I'm able to type this.

command found at:
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

