---
title: "GNOME Power Manager not installed correctly"
date: 2009-12-15
forum: General Help
---

### Post by ahayzen on 2009-12-15
Hi

I booted my Ubuntu 9.10 to recieve this message at the login screen.

'GNOME Power Manager not installed correctly. Please contact your system administrator.'

So I try to log in and this just chucks me back to the login screen.
If I use Gnome Failsafe it will hang.

I have tried all of these with no success:
```

sudo apt-get remove powermgmt-base
sudo apt-get install powermgmt-base

sudo dpkg --configure -a

apt-get --reinstall install gnome-power-manager

sudo rm -f /var/lib/gconf/defaults/*
sudo gconf-schemas --register $(ls /usr/share/gconf/schemas)

```

I have also tries creating a folder /var/lib/gconf/default/

Currently I can't login to my computer through gnome and only through terminal or via live cd.

Could anyone help me out?

Andy

---

### Post by sirex` on 2009-12-17
Same here:
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/441646](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/441646)

---

### Post by KPDXHAM on 2009-12-21
> **ahayzen said:**
> Hi

I booted my Ubuntu 9.10 to recieve this message at the login screen.

'GNOME Power Manager not installed correctly. Please contact your system administrator.'

So I try to log in and this just chucks me back to the login screen.
If I use Gnome Failsafe it will hang.

I have tried all of these with no success:
```

sudo apt-get remove powermgmt-base
sudo apt-get install powermgmt-base

sudo dpkg --configure -a

apt-get --reinstall install gnome-power-manager

sudo rm -f /var/lib/gconf/defaults/*
sudo gconf-schemas --register $(ls /usr/share/gconf/schemas)

```I have also tries creating a folder /var/lib/gconf/default/

Currently I can't login to my computer through gnome and only through terminal or via live cd.

Could anyone help me out?

Andy

Same error, but I believe I caused this one myself! For a few weeks now I've finally been enjoying Ubuntu without having a problem. Had it all tweaked-out the way I want it. Then, I decided I would just try to make a back-up using sbackup. All was going fine, far as I could tell since there's no GUI indicator showing the progress of the backup, well, I thought it was done and rebooted for whatever reason. It was looking like normal bootup until I got the same message 'GNOME Power Manager not installed correctly. Please contact your system administrator.'

Since then, I tried the following from the live Ubuntu 9.10 cd:

sudo rm -f /var/lib/gconf/defaults/*
sudo gconf-schemas --register $(ls /usr/share/gconf/schemas)

From this thread:
[http://ubuntuforums.org/showthread.php?t=785012](http://ubuntuforums.org/showthread.php?t=785012)

The reason this didn't work for me is that I don't know just how to "fill-in the blanks" so to speak.
It would be really great to be able to fix this present system, or at least retrieve my configuration and "stuff" that I've accumilated. If not, I'll just start over again. Lost count on how many times I've reinstalled Ubuntu in the past few months. I'm trying to get it set-up like we have xp on our 2 computers. If I could do without M$ I would, but at present it's almost like one step forward, two backward.](*,)

Dual Booting with WUBI

Main HDD Win XP

Slave HDD Ubuntu 9.10 (Primary Boot)

If there's someone out there that would help me either get this to boot normal, or retrieve my stuff, this would be greatly appreciated! :)

I've attached a screen picture showing my Ubuntu drive partition.
Let me know if you need more info.

Thanks,
Cliff

---

### Post by KPDXHAM on 2009-12-23
That's okay, I'll just reformat & start over again. I really like Ubuntu, but it's definitely more fragile than M$ XP PRO!

---

### Post by KPDXHAM on 2009-12-28
> **KPDXHAM said:**
> Same error, but I believe I caused this one myself! For a few weeks now I've finally been enjoying Ubuntu without having a problem. Had it all tweaked-out the way I want it. Then, I decided I would just try to make a back-up using sbackup. All was going fine, far as I could tell since there's no GUI indicator showing the progress of the backup, well, I thought it was done and rebooted for whatever reason. It was looking like normal bootup until I got the same message 'GNOME Power Manager not installed correctly. Please contact your system administrator.'

Since then, I tried the following from the live Ubuntu 9.10 cd:

sudo rm -f /var/lib/gconf/defaults/*
sudo gconf-schemas --register $(ls /usr/share/gconf/schemas)

From this thread:
[http://ubuntuforums.org/showthread.php?t=785012](http://ubuntuforums.org/showthread.php?t=785012)

The reason this didn't work for me is that I don't know just how to "fill-in the blanks" so to speak.
It would be really great to be able to fix this present system, or at least retrieve my configuration and "stuff" that I've accumilated. If not, I'll just start over again. Lost count on how many times I've reinstalled Ubuntu in the past few months. I'm trying to get it set-up like we have xp on our 2 computers. If I could do without M$ I would, but at present it's almost like one step forward, two backward.](*,)

Dual Booting with WUBI

Main HDD Win XP

Slave HDD Ubuntu 9.10 (Primary Boot)

If there's someone out there that would help me either get this to boot normal, or retrieve my stuff, this would be greatly appreciated! :)

I've attached a screen picture showing my Ubuntu drive partition.
Let me know if you need more info.

Thanks,
Cliff

**I'm back!**
I still think there should be a way to fix this problem OR at least be able to access my files from the system.
Is there ANYONE who knows how to do this, or that can point me in the right direction? Obviously I'm a newbie to Linux and would really appreciate the help.

Thanks

---

### Post by dpacmittal on 2010-04-12
Maybe this can fix your issue:
[http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)

---

### Post by marcos78 on 2010-04-23
I have tried this and solved my problem, Thanks [dpacmittal]("http://ubuntuforums.org/member.php?u=915607")

---

### Post by theronb on 2010-10-03
Had the same "Power Manager" error message and couldn't log in, found that the hard drive was 100% full. After much searching for answers, this worked for me: I opened a terminal (CTRL + ALT + F1), then cleaned out root trash, which was loaded with files from copying my photos to an external drive for backup:
[INDENT]sudo rm -r /root/.local/share/Trash/files
[/INDENT]and
[INDENT]rm -r /root/.local/share/Trash/info
[/INDENT]This dis the trick, then I also cleaned out trash for both user accounts.

---

