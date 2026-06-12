---
title: "sudo not working"
date: 2011-06-30
forum: General Help
---

### Post by davdo2004 on 2011-06-30
I can't run anything that requires sudo authentication. eg. If I try to run synaptic I get the password box pop up and I enter my password and nothing happens.

---

### Post by tcsmith1978 on 2011-06-30
can u look in/var/log/auth.log to see if there are any clues there?

---

### Post by haqking on 2011-06-30
> **davdo2004 said:**
> I can't run anything that requires sudo authentication. eg. If I try to run synaptic I get the password box pop up and I enter my password and nothing happens.


are you in the sudo group, do you or have you had sudo permission before.

When or what changed ?

---

### Post by davdo2004 on 2011-06-30
Just tried to open synaptic in terminal and this came up in /var/log/auth.log   ........

Jun 30 13:46:34 dad-desktop sudo: pam_unix(sudo:auth): auth could not identify password for [dad]
Jun 30 13:46:34 dad-desktop sudo:      dad : 3 incorrect password attempts ; TTY=unknown ; PWD=/home/dad ; USER=root ; COMMAND=/usr/sbin/synaptic

---

### Post by davdo2004 on 2011-06-30
> **haqking said:**
> are you in the sudo group, do you or have you had sudo permission before.

When or what changed ?

How do I find out if I am in the sudo group ? I have not had a problem ever since I installed ubuntu 10.04 when it first came out and as far as I am aware I have made no changes.

---

### Post by haqking on 2011-06-30
from terminal type :

groups <username>

it will list groups you are in such as adm (admin)

or you can view the sudoers file with

gksudo gedit /etc/sudoers

you cannot edit unless you use visudo though.

Dont edit unless you what you are doing

sudoers file man page at [http://manpages.ubuntu.com/manpages/lucid/en/man5/sudoers.5.html](http://manpages.ubuntu.com/manpages/lucid/en/man5/sudoers.5.html)

---

### Post by davdo2004 on 2011-06-30
Thanks for your help haqking

The group command gives me   dad : dad adm dialout cdrom plugdev lpadmin admin sambashare

I can't view the sudoers file because when I enter the password nothing happens.

---

### Post by haqking on 2011-06-30
can you post some output or errors ?

example from terminal:

supply the wrong password for sudo and post the error message if any you get ?

and have you enabled the root ? so that sudoers file can be edited if need be ?

---

### Post by evilbrent on 2011-06-30
davdo - I recently had the same problem and I'm trying to remember how I fixed it.

What did you do to break it do you know?

---

### Post by haqking on 2011-06-30
try this thread

[http://ubuntuforums.org/showthread.php?t=1309269](http://ubuntuforums.org/showthread.php?t=1309269)

---

### Post by davdo2004 on 2011-06-30
If I enter the wrong password it just says sorry,try again. If I enter the correct password nothing happens at all.
I'm sorry, I don't know how to enable the root. I could get into a root console from recovery mode but I don't know what commands to enter.

---

### Post by evilbrent on 2011-06-30
[http://ubuntuforums.org/showthread.php?t=1785262](http://ubuntuforums.org/showthread.php?t=1785262)

The help I got here solved my problem. Might work for you??

Basically you can boot into grub (googlable) to get root access which can give you access to the sudoers file.

Then I typed in these commands (don't ask me where I found them), which fixed my sudo.

```
chown root:root /etc/sudoers 
chmod 440 /etc/sudoers
chown -R root:root /etc/sudoers.d
chmod  755 /etc/sudoers.d 
chmod  440 /etc/sudoers.d/*
```

---

### Post by davdo2004 on 2011-06-30
> **evilbrent said:**
> [http://ubuntuforums.org/showthread.php?t=1785262](http://ubuntuforums.org/showthread.php?t=1785262)

The help I got here solved my problem. Might work for you??

Basically you can boot into grub (googlable) to get root access which can give you access to the sudoers file.

Then I typed in these commands (don't ask me where I found them), which fixed my sudo.

```
chown root:root /etc/sudoers 
chmod 440 /etc/sudoers
chown -R root:root /etc/sudoers.d
chmod  755 /etc/sudoers.d 
chmod  440 /etc/sudoers.d/*
```


I'm afraid doing all that has made no difference. Thanks anyway for your help.

---

### Post by twowheels on 2011-06-30
How About backing up HOME Directory  and reinstall

---

### Post by haqking on 2011-06-30
you could try this ?

Turn your computer on. Press ESC at the grub prompt.
 Press e for edit.
 Highlight the line that begins kernel ………, press e
 Go to the very end of the line, add **rw init=/bin/bash**
 press enter, then press b to boot your system.
 Your system will boot  to a root shell without password

 Type in passwd  username
 Set your password.
 the type reboot ?

---

### Post by haqking on 2011-06-30
have you tried changing your password ?

passwd <username>

then log out, i would actually reboot too jjst to make sure.

then try again ?

---

### Post by davdo2004 on 2011-06-30
> **haqking said:**
> you could try this ?

Turn your computer on. Press ESC at the grub prompt.
 Press e for edit.
 Highlight the line that begins kernel ………, press e
 Go to the very end of the line, add **rw init=/bin/bash**
 press enter, then press b to boot your system.
 Your system will boot  to a root shell without password

 Type in passwd  username
 Set your password.
 the type reboot ?

Yes I have done that and rebooted, I have it set to log in automatically which works fine, but if I then log out and try to log back in nothing happens and I have to restart the computer. Feeling very frustrated at the moment.

---

### Post by haqking on 2011-06-30
> **davdo2004 said:**
> Yes I have done that and rebooted, I have it set to log in automatically which works fine, but if I then log out and try to log back in nothing happens and I have to restart the computer. Feeling very frustrated at the moment.


have you just tried changing your password ?

also remove auto login for now as we are messing with passwords

---

### Post by davdo2004 on 2011-06-30
I have changed the password again, removed auto login and when I get to the login screen and type in the password it just greys out and nothing happens. If I enable autologin in etc/gdm it auto logs in fine.

---

### Post by haqking on 2011-06-30
> **davdo2004 said:**
> I have changed the password again, removed auto login and when I get to the login screen and type in the password it just greys out and nothing happens. If I enable autologin in etc/gdm it auto logs in fine.


mmm without being sat there i would of been inclined to restore my backup by now ;-) and would of been done hours ago LOL

Unless someone else chimes in with other ideas or options then hopefully you have a backup ;-)

---

### Post by davdo2004 on 2011-06-30
I will just leave it as it is for now, a bit of a pita to go to a root shell to do anything that requires that authority but I don't fancy reinstalling just yet.
Many thanks for your efforts to help me.

---

