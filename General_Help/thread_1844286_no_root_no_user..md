---
title: "no root no user."
date: 2011-09-14
forum: General Help
---

### Post by amerinde on 2011-09-14
ok, long story short, i am trying to install a program, just upgraded to the new ubuntu (i think 11.04??). the program wouldnt install under my user name, nor did it work for me when it installed with sudo. so i went to users and made myself root.
 
now when i sign on, i get no desktop, it is blank. i get a nautalus error, saying it cant create my desktop, and if i try to sign on as root, my password is refused... can someone help?

---

### Post by haqking on 2011-09-14
> **amerinde said:**
> ok, long story short, i am trying to install a program, just upgraded to the new ubuntu (i think 11.04??). the program wouldnt install under my user name, nor did it work for me when it installed with sudo. so i went to users and made myself root.
 
now when i sign on, i get no desktop, it is blank. i get a nautalus error, saying it cant create my desktop, and if i try to sign on as root, my password is refused... can someone help?


Logging in as Root is not supported under the canonical model as it is locked by default.  I am a little confiused when you say you made yourself root, or do you mean you unlocked the exisiting root account ?

When you were denied sudo permission were you entering your own password when prompted ?

see [ROOTSUDO]("https://help.ubuntu.com/community/RootSudo")

and were you in the sudo group before ?

see here to fix sudo if it has issues [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by amerinde on 2011-09-14
ok, i am on a windows machine right now, so i dont have the exact wording. i am trying to install a program that needs roots permission to install to certain folders under my user name. i tried sudo, and i tried to copy the files to the folder, but the folder is only accesible by root. so i went to users, like in control panel of windows, i made a (tick) to make me root. rebooted, now i cant get back on. i now get a nautilus error

---

### Post by C.Ganesh on 2011-09-15
which version of ubuntu are you using?coz i didnt find any such thing to enable root account in 11.04

---

### Post by fdrake on 2011-09-15
i am a little confused :

1.Sudo gives you FULL root permissions, so whatever you need to do with the program, sudo should have handle it.

2.when you say I made root, i think you just created a new user(low level) with the name of root, you actually did not enable the real root user at all. The user probably does not have a Dekstop folder or any configuration folder(like gnome/nautilus/Xorg ...). To check this please run these commands and post here the results:
```
sudo ls /home
sudo less /etc/passwd | grep -i root
```

3. it looks like that you cannot login to your old username anymore
please try Cntrl+Alt+f1(or f2,f3,f4..) and try to login and run those commands above.

---

### Post by amerinde on 2011-09-15
errors i get now..
 
1. could not update ICEauthority file /homr/william/.ICEauthority
 
Close
 
2. there is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 with status 256)
 
Close
 
nautilus could not create the following required folders:/home/william/desktop. /home/william/.nautilus
 
ok

---

### Post by fdrake on 2011-09-15
do you have important files in your ubuntu partition? Is this a wubi install or a full dualboot system? can you back up your data and reinstall the system?

edit:
also have you tried to reinstall the desktop
```

sudo apt-get install --reinstall ubuntu-desktop

```

---

### Post by 3rdalbum on 2011-09-15
Don't ever "make yourself root"; as you've probably realised, you can really stuff things up.

If a program is installing only to your home directory, you shouldn't need 'sudo'. If you do, it's because some folders in your home directory have been created using 'sudo' already - in other words, a mistake you might have made earlier.

If I was in your situation, I would boot into recovery mode. Reboot and select the second option in your GRUB menu, which includes the words "(Recovery Mode)". I think this brings you a text-only terminal as root.

Type in the following, substituting the word 'username' for your actual username:

```
chown -R username /home/username
chmod -R u+rw /home/username
```

The first command makes your home directory and all its contents (recursively) "owned" by your user account. This fixes the problem of root-owned files and folders there. The second command makes sure your user account has read and write permission to your home directory and all its contents.

Typing 'reboot' afterwards, and then booting back into the regular Ubuntu mode, should be okay.

[SIZE="4"]Disclaimer:[/SIZE] I have a niggling feeling that I'm missing something, or that there might be one or two files in your home directory that are meant to stay root-owned. However, in lieu of current advice, my suggestion should probably get your system working again.

Just try not to fiddle with permissions again, and try not to use 'sudo' unless really necessary. :-)

Good luck!

---

### Post by Zephilinox on 2011-09-15
I'm pretty sure what he did was add his user to the group "root" in the "Users and Groups" panel.

---

