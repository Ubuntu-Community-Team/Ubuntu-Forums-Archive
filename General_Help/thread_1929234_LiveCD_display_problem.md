---
title: "LiveCD display problem"
date: 2012-02-21
forum: General Help
---

### Post by johncmolyneux on 2012-02-21
I'm trying to install Ubuntu 11.10 onto a secondary partition.  When I boot from the ~Live CD I get an initial purple screen with a couple of small icons at the bottom (keyboard and a person), and then this changes to something that looks like a corrupted display (similar to when you set the resolution to something your monitor can't display and you just basically get a bunch of moving diagonal lines).

Could someone please advise me what to do about this?  I thought just burning the iso to a CD (or DVD) would be enough to boot from it and the display would just work.

**Edit:** I just pressed escape at the first screen with the 2 small icons and it showed me the boot menu.  I selected to install it and got the same corrupted display, so that doesn't help.

---

### Post by ajgreeny on 2012-02-21
Boot to the live CD again and get to that same boot menu for "Try" "Install" etc etc.  Now hit F6 and choose the boot options one by one starting with nomodeset, and you may get the system to boot to a desktop that you can use.

If that works you could also boot to your installed version, go to a command line with Ctrl+Alt+F1 and then log in with username and password (password will not show on screen; type it and just hit "Enter")

Now use command ```
sudo nano /etc/default/grub
``` look for the line ```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet"
``` and add nomodeset so it looks like ```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet nomodeset"
```and then reboot with ```
sudo shutdown -r now
```

---

### Post by johncmolyneux on 2012-02-22
Thanks a lot man.  With the info you gave me I was able to boot into the LiveCD, so I knew using "nomodeset" was the correct way to go.  I installed it but then had to edit grub in the installation, rather than by running the CD.  I had to go into recovery mode to do that and with a bit of tweaking I got it to dual boot perfectly.  I'm now posting this from Chromium, running on Ubuntu.

Thanks a lot for your help :)

---

### Post by ajgreeny on 2012-02-22
Well done and welcome!

Glad to be of help.

---

