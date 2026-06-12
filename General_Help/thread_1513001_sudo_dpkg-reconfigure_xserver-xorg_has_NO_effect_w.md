---
title: "sudo dpkg-reconfigure xserver-xorg has NO effect whatsoever"
date: 2010-06-18
forum: General Help
---

### Post by Soman23 on 2010-06-18
Hey.. newbie here, I have used Linux in the past but it has come a LOOONG way, obviously.  Running a quad core Intel with the latest Ubuntu on the latest version of VirtualBox.  Soundcard recognition seemed to be no issue for this setup, but unfortunately not video..

I have looked up ways to change my screen resolution many times now, to no avail.  None of the ways I've tried have worked. In the 'Monitor' section I am only given two options, 800x600 and 640x480, both at 4:3 which is totally absurd..  Ubuntu doesn't recognize the monitor (Samsung Touch Of Color T260HD 25.5-Inch LCD HDTV Monitor) This is the most common terminal command I see on the subject:

sudo dpkg-reconfigure xserver-xorg

It literally has no effect, even though my user account has full admin access and can execute sudo commands, I already checked. (I am taken right back to: 

<user>@<user>-desktop:~$

Yet pages like this one (if you scroll down to #33) make it seem like I'll be taken into a little screen where I can arbitrarily modify the resolution:

[http://www.simplehelp.net/2007/05/13/how-to-install-ubuntu-studio-in-windows-using-virtualbox-a-complete-walkthrough/](http://www.simplehelp.net/2007/05/13/how-to-install-ubuntu-studio-in-windows-using-virtualbox-a-complete-walkthrough/)

This is not the case.  Nothing happens at all, with that command or variations of that command, except for being prompted for the sudo password (which doesn't seem to fail, or it would tell me so).

Please.. someone help! I will be so grateful.. and maybe when I learn enough about Ubuntu I can return the favor again some day in the future.  It'd be nice to not be running this OS on a tiny little box when I have a friggin' 26" screen.  I realize widescreen may not be achievable but even just to fill the square portion would be great..

---

### Post by kerry_s on 2010-06-18
yeah, that command is like 2-3 years old.
the way its done now is to switch to another tty(ctrl+alt+f2), kill gdm(sudo service gdm stop) & run-> X -configure
to get a xorg.conf for your system, which then needs to be copied to /etc/X11/xorg.conf

you can also do it from the recovery mode root shell.

---

### Post by Soman23 on 2010-06-18
Thanks.. amazing how fast these commands change sometimes.

Ok so I got as far as killing gdm.  Can't seem to find the new way to run a process (did it change?)  I don't think I'll have a problem copying the file though, doesn't seem like that command has changed as well.

---

### Post by kerry_s on 2010-06-18
> **Soman23 said:**
> Thanks.. amazing how fast these commands change sometimes.

Ok so I got as far as killing gdm.  Can't seem to find the new way to run a process (did it change?)  I don't think I'll have a problem copying the file though, doesn't seem like that command has changed as well.

what do you mean?

you just do this in order:
[B]ctrl+alt+f2
log in
sudo service gdm stop
sudo X -configure
sudo cp /root/xorg.conf /etc/X11/xorg.conf
sudo reboot[/B]

(i'm not sure about /root/xorg.conf it might be xorg.conf.sample, just make sure you read what it tells you)
after it reboots you can edit it in the gui.
[B]alt+f2
gksudo gedit /etc/X11/xorg.conf[/B]

---

