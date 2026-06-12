---
title: "Ubuntu 10.04 cannot boot after hard reset."
date: 2010-05-27
forum: General Help
---

### Post by silkworm2.5 on 2010-05-27
Hi People.
I have  Wubi install of Ubuntu 10.04 on Windows XP Home.
XP has crashed and refuses to boot, so i had to do a hard reset. Now neither system will boot. Ubuntu comes up with some sort of terminal page, and windows just stays at the boot screen with the booting bar.
What should I do?

---

### Post by bodhi.zazen on 2010-05-27
Start with checking your hard drive for errors.

As for Windows, I suggest you ask on a Windows forum.

As for Ubuntu, can you give a better description of what happens when you boot Ubuntu ?

Is there an error message of some kind ?

When you say command line, what do you mean ? What does the prompt say ? and what error message did you get ?

---

### Post by searchfgold6789 on 2010-05-27
Yes, more info would be helpful. Windows crashed you say, so check your hard disk for errors:
boot from the windows XP CD and press r once everything loads.
Log into the correct partition, which has WINDOWS written on it, and type 
```
chkdsk c:\
fixboot c:\
```

IF this is what I think it is, you may have to also type
```
fixmbr
exit
```
and reinstall ubuntu, because ubuntu can be sensitive to crashes.

If someone else here posts and tells you how to fix Ubuntu but you can't fix windows, then just do the chkdsk and fixboot as mentioned above, and that should get windows to work again.

---

### Post by silkworm2.5 on 2010-05-27
I'll look at and note down the message that appears.

When booting Ubuntu, it goes to the splash screen with the title and five orange lights lighting in sequence, then comes up with a command prompt. I will report back shortly with more details of that.

---

### Post by silkworm2.5 on 2010-05-27
OK, Noted down all that appeared.

Mount: Mounting /dev/loop0 on /root Failed: device or resource busy
Mount: Mounting /dev on /root/dev failed: No such file or directory
Mount: Mounting /sys on /root/sys failed: No such file or directory
Mount: Mounting /proc on /root/proc failed: No such file or directory

Target file directory does not have /sbin/init

No init found. Try passing init=bootarg

Busy Box V1.13.3 (Ubuntu 1:1.13.3-1 Ubuntu11) Built in shell (Ash)

Enter help for a list of built in commands

(Intram FS) _

:confused::confused::confused:

---

### Post by bodhi.zazen on 2010-05-27
Try the commands searchfgold6789 gave you.

If they fail, you may have had damage to your harddrive or ntfs partition.

Essentially this is a Windows problem, and because you used wubi, ubuntu was taken down with windows.

Again, we are trying to encourage Windows questions to Windows forums.

If you can not recover windows, you may need to reinstall both windows and Ubuntu.

If you are going to use Ubuntu long term, I suggest a standard install rather then wubi.

You may need to replace your hard drive, not sure yet.

---

### Post by louismurphy on 2010-05-27
[COLOR=#000000][FONT=Times New Roman][FONT=Lucida Grande]The graphical interface used in Ubuntu comes in two parts: X and GNOME. The X server is an underlying chunk of software that ensures your graphics card and monitor work, and it provides a base for GNOME to run on. The GNOME desktop uses X as an engine to create the rich desktop platform you have been using. If you start the computer and you can only see text and no graphical interface, this is a problem with X.
First, reboot your computer to see if that fixes the problem. When your computer has booted, if you still have the same problem, Ubuntu may have told you that it cannot start X. If you did not see this message, press Ctrl-Alt-F7 to see if you can access the graphical interface. If this does not work, there is a configuration problem with X.
X stores its configuration in /etc/X11/xorg.conf. Before you fiddle with your configuration, it is always wise to make a backup of the file. Even if X is not starting, some other parts of the configuration may be working fine.
foo@bar:~$ cd /etc/X11
foo@bar:~$ sudo cp xorg.conf xorg.conf.old
First you move to the /etc/X11 directory and then you use the cp command to copy the existing file (xorg.conf) to a backup file (xorg.conf.old). You now have both an xorg.conf and an xorg.conf.old with the same information in them.
Now run the X configuration process:
foo@bar:~$ sudo dpkg-reconfigure xserver-xorg
A configuration routine will start, and you should experiment with different settings in the routine. Unfortunately, we don't have the space to cover X configuration in detail, so refer to[https://wiki.ubuntu.com/debuggingxauto](https://wiki.ubuntu.com/debuggingxauto) configuration.
[/FONT][/FONT][/COLOR]

---

### Post by silkworm2.5 on 2010-05-31
Hey guys.
I managed to fix it. sort of...
I had a disc called the 'ultimate boot CD' and booted that and tried out some of its tools. A came to a tool caller Avira (?) or something similarly titled which scanned the drive for errors. After 5 hours of scanning, it had repaired over 1500 errors and the computer was able to boot again. Now i have re-installed ubuntu, but cannot do the chkdsk /f command. It says it cannot access the drive directly and refuses to do anything. Ubuntu is fine though, running smoothly, without lag, and efficiently, and it is only windows that as a problem. If no-one here can help I will go to a windows forum, but just in case, does anyone know what to do?

---

### Post by louismurphy on 2010-06-17
do you reset your BIOS ? Have you tried this? [IMG]http://xd2.us/im/smile.gif[/IMG]

---

