---
title: "numlockx not setting numlock state"
date: 2011-01-15
forum: General Help
---

### Post by mmmmna on 2011-01-15
I've already tried this stuff: [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock) and it does not work as described in that topic: the numbers portion of my keyboard is not active when I get to the login prompt of KDM. I use numbers in my password, I wish to use the number pad of my keyboard to enter number portions of my password when I am at the KDM login prompt. The numlock key is what operates this section of the keyboard, and at present, at the KDM login screen, the numlock LED is off AND I cannot enter numbers as I press the numbers on the number pad. I can press the numlock key and the number portion of my keyboard works just fine. My BIOS sets the numlock on. The numlock LED is on during the grub menu. Since this numlock function is modified during the boot sequence BEFORE the KDM login screen, the KDM setting is _not_ where I should make a change.

***I want the numlock to be turned on and left that way.***

I boot _Kubuntu 10.04 LTS for 64 bit desktop_. I do **not** use Gnome, so configuring GDM is a wrong path. I use KDM, but before you post, know this: I have already visited K Menu - Applications - Settings - System Settings, and set the Computer Administration - to "Turn on" NumLock on KDE startup, but that setting will only activate numlock **AFTER** I log in. As stated earlier, before I get to the KDM login screen, the numlock LED has been turned off.

***I want the status of my numbers keys to be left alone when the Kubuntu system boots, since my BIOS properly sets the numlock status EXACTLY as I want the numlock to be set.***

I have a PS/2 keyboard, and I will likely change to a USB keyboard in a few months as this PS/2 keyboard is getting rather old. Solutions that address both situations would be appreciated by anyone that reads this thread, but my present goal is PS/2.

My question is: Which file should someone edit regarding the keyboard initialization so as to leave the numlock setting alone, which, IMO, should be to leave the keyboard as the BIOS sets it, especially in regards the numlock? What does one need to enter at the specified location?

Repeat: I've tried this stuff: [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

I've read the following thread:
[http://ubuntuforums.org/showthread.php?t=1615970&highlight=numlock](http://ubuntuforums.org/showthread.php?t=1615970&highlight=numlock)
so pardon me if reading 250 threads is equated with obfuscation.

---

### Post by mmmmna on 2011-01-23
[http://ubuntuforums.org/showthread.php?t=1615970](http://ubuntuforums.org/showthread.php?t=1615970) post #3 pointed me towards [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock) (Yes, I went back and re-read something).

My solution was to become root and edit the /etc/kde4/kdm/Xsetup file to add```
if [ -x /usr/bin/numlockx ]; then
  /usr/bin/numlockx on
fi
```
numlock is on as KDE login manager appears.

PS: From what I've seen when booting Kubuntu 10.04 64 bit, the numlock setting gets turned off very early in the boot process, so possibly some point, between presenting GRUB kernel entries and launching startx, needs to be tweaked as well (to not change the numlock state). The BIOS is set for numlock on, and then the boot process turns off the numlock before the KDM login manager appears. I often take the position that the user (sys admin) is the one who should define what is acceptable, yet there never seems to be any "Q and A" about this setting during distro installation. Sorry if that seems petty.

---

