---
title: "Help! - I need my computer back (broken pipes)"
date: 2012-10-10
forum: General Help
---

### Post by moodle on 2012-10-10
Hello,

I have been using *buntu operating systems since 2008. Usually manage to find my way around any small problems through the forums, but this one has me stumped.

During boot-up, I get the following error message:

could not write bytes broken pipe 
* Stopping anac(h)ronistic cron 
saned.
* Stopping save kernel messages
* Starting anac(h)ronistic cron 
* Stopping anac(h)ronistic cron 
* Checking battery state
* Sping system v runlevel compatibility

What's going on? I've tried many solutions including:

Deleting some hidden folders in the home directory, as explained here:
[http://askubuntu.com/questions/129888/crash-during-12-04-upgrade-broken-pipe-cannot-boot](http://askubuntu.com/questions/129888/crash-during-12-04-upgrade-broken-pipe-cannot-boot)

Installing Nvidia drivers (even though I don't have an Nvidia graphics card, I have a Thinkpad X61, which has all compatible hardware with ubuntu)

Uninstalling and reinstalling  xserver-xorg

Fixing broken dependencies with sudo apt-get -f install



I can get to a terminal pressing ALT+CTRL+F1. Until I reinstalled xserver-xorg, I could type "startx" and it would take me to my desktop, but with a different background and different menu from my custom settings. Since I reinstalled xserver-xorg, I just get a blank screen when I type "startx".

This is so frustrating! I need to work! What's happening? Why has this happened? Can I get my files back? How can I fix it?

I am running Xubuntu 12.04.

Thank you.

---

### Post by newb85 on 2012-10-10
Hmm...let me reassure you, your files are not lost.  Don't take my word for it; boot from a Live CD or USB and try browsing your files.  If the files are important to you, it would be a good idea at this point to plug in an external HD and create a backup copy of them there.

---

### Post by moodle on 2012-10-10
Thanks - I'll do that to get the files.

What can I do to fix the system? I'd really rather not do a fresh install. Why has this happened?

Why can't Linux just work? Everytime I've installed it for myself or others, there have been problems.

---

