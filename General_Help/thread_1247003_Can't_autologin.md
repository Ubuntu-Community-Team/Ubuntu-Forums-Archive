---
title: "Can't autologin"
date: 2009-08-22
forum: General Help
---

### Post by abelthorne on 2009-08-22
Hello,
I have a PC with Ubuntu Server installed. As I sometimes need a GUI for specific operations (which I can manage through VNC), I installed the ubuntu-desktop package on it and set up the automatic login.
Then, I wanted to test Xfce rather than GNOME and installed xubuntu-desktop. Finally, I came back to GNOME and uninstalled xubuntu-desktop and all packages I could find that were related to Xfce.

Since I've installed xubuntu-desktop, autologin at GDM doesn't work anymore, I always end up on the login screen and have to manually enter my login/password. Well, it sometimes work but very rarely and it seems to be random.
Since it's a PC on which I want to remove the monitor I currently have, it's a bit annoying as I want it to boot automatically into GNOME.

I've checked /etc/gdm/gdm.conf-custom and the options AutomaticLogin & AutomaticLoginEnable are set.

Any idea ?

EDIT : found [a bug report on Launchpad](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/370541). Msg #33 seems to fix the problem :

sudo update-rc.d -f gdm remove
sudo update-rc.d gdm defaults

---

### Post by borm on 2009-09-03
> **abelthorne said:**
> Hello,
I have a PC with Ubuntu Server installed. As I sometimes need a GUI for specific operations (which I can manage through VNC), I installed the ubuntu-desktop package on it and set up the automatic login.
Then, I wanted to test Xfce rather than GNOME and installed xubuntu-desktop. Finally, I came back to GNOME and uninstalled xubuntu-desktop and all packages I could find that were related to Xfce.

Since I've installed xubuntu-desktop, autologin at GDM doesn't work anymore, I always end up on the login screen and have to manually enter my login/password. Well, it sometimes work but very rarely and it seems to be random.
Since it's a PC on which I want to remove the monitor I currently have, it's a bit annoying as I want it to boot automatically into GNOME.

I've checked /etc/gdm/gdm.conf-custom and the options AutomaticLogin & AutomaticLoginEnable are set.

Any idea ?

EDIT : found [a bug report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/370541"). Msg #33 seems to fix the problem :

sudo update-rc.d -f gdm remove
sudo update-rc.d gdm defaults

Their solution did not work for me.  The assertion was that gdm was launched before the automatic login could be processed, therefore causing the autologin to fail.  When I updated gdm to the default priority, it ended up launching even earlier in the process.  I tried it anyhow, and it failed.

The root cause struck me as correct, however, so I changed gdm startup position from 20 to 99 in all of the run levels where it was started, and now my autologin works just fine.  Refer to the update-rc.d manpage for details on how to do this.

As a backup solution, I also enabled timed login with a 10 second delay.  If, for some reason, the auto login fails, the timed login will take care of it 10 seconds later.  

So far, in the 3 days since I changed the priority, autologin has worked correctly every time.  I hope this helps.

  --Eric

---

