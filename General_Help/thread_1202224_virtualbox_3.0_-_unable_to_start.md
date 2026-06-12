---
title: "virtualbox 3.0 - unable to start"
date: 2009-07-02
forum: General Help
---

### Post by PerfectReign on 2009-07-02
Today, VB 3.0 came out. I went and downloaded the version from the Sun website.

I then installed it.

I am unable to run. Just to check that it was installed, I ran a dpkg -i - what's going on?

[COLOR=Blue]kai@r2d2:~/downloads$ sudo dpkg -i virtualbox-3.0_3.0.0-49315_Ubuntu_jaunty_i386.deb
[sudo] password for kai: 
(Reading database ... 194958 files and directories currently installed.)
Preparing to replace virtualbox-3.0 3.0.0-49315_Ubuntu_jaunty (using virtualbox-3.0_3.0.0-49315_Ubuntu_jaunty_i386.deb) ...
 * Stopping VirtualBox kernel module                                                                                                 *  done.
Unpacking replacement virtualbox-3.0 ...
Setting up virtualbox-3.0 (3.0.0-49315_Ubuntu_jaunty) ...
addgroup: The group `vboxusers' already exists as a system group. Exiting.
 * Starting VirtualBox kernel module                                                                                                 *  done.

kai@r2d2:~/downloads$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
kai@r2d2:~/downloads$ 
[/COLOR]

---

### Post by kpkeerthi on 2009-07-02
The command is **V**irtual**B**ox

---

### Post by brydonhunter on 2009-07-02
I have run into the same issue, I reinstalled it and everything worked fine.

Good luck.

---

### Post by PerfectReign on 2009-07-02
Okay, got it, thanks!  It is VirtualBox.  I had tried to figure that out. 

Oddly enough, the icon for launching wasn't there last night. It is now.

Go figure!  #-o


in any case, I have it runnning just fine now. I use Windows 7 often in my work so it is a daily thing running on my laptop.

[IMG]http://www.perfectreign.com/stuff/2009/20090702_vb3_ubuntu.jpg[/IMG]

---

### Post by scorp123 on 2009-07-02
> **PerfectReign said:**
>  Oddly enough, the icon for launching wasn't there last night. It becomes visible after you logout and login again. Some settings need to be re-read I guess. Or something like that. That's why you see it now: You logged out, you shutdown your computer. When you logged in again all the required settings were re-read again and voila, you get the icon now.

Or you do it my way ... You kill parts of your GNOME session forcing the process to reload ... and voila, the icon will be there too now.
```
killall -1 gnome-panel
```

The "kill" or "killall" command with the "-1" (= minus one) switch tells a program "go shoot yourself ... and then come back again!" -- so a program will terminate, sync, and then re-read its config files and come back up again.

It's a nice way of getting stuff restarted without having to logout and it usually works for most programs.

---

### Post by PerfectReign on 2009-07-02
heh, so I should have done the Windows-thing and rebooted, then, eh? 

I'lll make a note of the killall command. Hadn't needed to use this before. (Though, I'm more familiar with KDE 3.x, having used that for several years.)

---

### Post by scorp123 on 2009-07-02
> **PerfectReign said:**
>  heh, so I should have done the Windows-thing and rebooted, then, eh?  Just logout and login again. That would be enough. A complete system reboot would be overkill. But yes, it would work too. It did work in your case.

> **PerfectReign said:**
>  I'll make a note of the killall command. Know thy terminal ;)

> **PerfectReign said:**
>  I'm more familiar with KDE 3.x "kill" and "killall" are system commands and independent of the GUI.

---

