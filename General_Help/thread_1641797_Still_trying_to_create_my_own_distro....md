---
title: "Still trying to create my own distro..."
date: 2010-12-09
forum: General Help
---

### Post by Stray Wolf on 2010-12-09
In Ubuntu Customization Kit I get this error:

sudo: no tty present and no askpass program specified

So, I read up and found I could try oem-config-remaster which I installed through the USC (Ubuntu Software Center).  I couldn't find the software in any menu so I tried to open it through the terminal.  Here's the intel:

me@myubuntu-laptop:~$ sudo oem-config-remaster
Usage: /usr/sbin/oem-config-remaster [-i gpg-key-id] [-t cd-title] [-o output-file] [-r extra-repository] [-e early-command] [-l late-command] cd-image packages
mount: can't find /tmp/tmp.g8EACcm5cZ in /etc/fstab or /etc/mtab
Cleaning up.
umount: /tmp/tmp.g8EACcm5cZ: not mounted

Update:  UCK is to much trouble since I got it working.  (Termnal sudo uck-gui).  I was hoping it would build off of my system.  Instead i just have to manually install onto it but that doesn't include configs...

So, I tried again:
me@myubuntu-laptop:~$ sudo oem-config-remaster
Usage: /usr/sbin/oem-config-remaster [-i gpg-key-id] [-t cd-title] [-o output-file] [-r extra-repository] [-e early-command] [-l late-command] cd-image packages
mount: can't find /tmp/tmp.wNXya944XV in /etc/fstab or /etc/mtab
Cleaning up.
umount: /tmp/tmp.wNXya944XV: not mounted
All done.

I just want to create my own installable LiveCD or LiveUSB that includes cairo-dock - how I have it configured and a theme I made for it, compiz - how I have it configured and a theme I made for it, along with the Restricted Extras, Sun Java, digikam, skype, hulu desktop and pidgin.  Seems easy enough...  Nothing I've tried works.

---

### Post by threegremlins on 2010-12-12
I'm having the same problem then found this on the uck launchpad
[http://fabrizioballiano.net/2007/11/27/remastering-an-ubuntu-alternate-iso-with-ubuntu-customization-kit-the-complete-guide/](http://fabrizioballiano.net/2007/11/27/remastering-an-ubuntu-alternate-iso-with-ubuntu-customization-kit-the-complete-guide/)
hope it helps

---

### Post by Stray Wolf on 2010-12-13
Thanks.  I may try another way since it doesn't seem like UCK let's me save configurations or add repositories.  I'll keep exploring though.

---

### Post by threegremlins on 2010-12-14
I've only been looking into UCK or customizing my own setup disk. I switched to Crunchbang(staying in the Debian family) but missed some of the little features Ubuntu has like jockey-gtk and Ubuntu is easier to install. I came across A Bare Bones Ubuntu install a while back and looked into it again.

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

I think he's a moderator here on the forum, I used his method of installing the minimal distribution Mini.iso. Where I differ is now I use apt-get in a shell script to install first xorg xterm openbox obconf obmenu tint2 menu gksu synaptic. I reboot, run startx then reboot again, at the command line I run the second shell script to download and install the rest of the programs. It takes about an hour on highspeed.

The only drawback is you can't successfully upgrade, the upgrade manager changes things to a normal Gnome type install. Sometimes you just can't win, so I either stick with the long term Lucid install or re-install every six months to stay current. I like the way I have it now so I'm willing to do it.

It's easier if you have your if you have your root and home on different partitions then all you have to do is replace your tweaks with the installed ones, which takes me about another fifteen minutes. On a USB you can use the box you used to install your system to access the tweaks.

Still though, I'd like to figure out how to make UCK work now that it's caught my attention.

---

