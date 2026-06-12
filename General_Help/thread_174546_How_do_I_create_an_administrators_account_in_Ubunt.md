---
title: "How do I create an administrators account in Ubuntu?"
date: 2006-05-12
forum: General Help
---

### Post by muffinhead on 2006-05-12
While I'm figuring out how to fix the hotplug subsystem problem, I've been fooling around with Ubuntu.

Firt thing is, during install it didn't ask me to Create an Administrators account, or superuser. It only asked me if I wanted to create a "Normal users account", after I supplied the root password. 

I need superuser, or Administrative Privileges, because it say's I can't view the contents on my hard drive, modify, or add files/folders, because I don't have sufficient privileges to do so.

I can't access users, via the admin panel, It acts like it's starting up, and then quits, I'm guessing it's because I don't have sufficient privileges.

I've tried logging in as root, but when I try to log in, via the  bash shell, it cannot startx, because of something with xorg (not sure if it's xorg).

If anyone could be so kind as to tell me how to create a superuser, or administrators account, and log in as an admin, I'd really appreciate it, Thank You:)

---

### Post by aysiu on 2006-05-12
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by muffinhead on 2006-05-12
Thanks, but I tried that, and It doesn't work. I tried "gksudo nautilus" , a password box did pop up, however it didn't give me root privileges within that window.

Using the command "Sudo" along with the desired Directory/File I want to open, doesn't open the file/program , instead below where I typed, Ex. sudo /etc/X11/xorg.conf, it comes up with my username "User@Ubuntu$"

Whenever I type just /etc/X11/xorg.conf , I can view the file in nano, and edit it, but when I go to save it, I get a "permission Denied" Message, resulting in it not saving.

If you could help me again, I'd really appreciate it, Thank You:)

---

### Post by jrib on 2006-05-12
Did you do an expert install?

Actually, first... do these commands work:

sudo echo hi
sudo nano /etc/X11/xorg.conf

---

### Post by muffinhead on 2006-05-12
No, those don't work, as I can't use "sudo", however "su" works fine as in su /etc/X11/xorg.conf etc.. and gksu nautilus 

Yes I had to do an expert-installation, becuse my DVD-RW Drive required that DMA be enabled, which is not enabled by default in Ubuntu, or else it could'nt read the CD-Rom Correctly, and resulted in errors.

Also I downloaded the HSF Dial-Up modem driver's  from the linuxant website for ubuntu Breezy Badger kernel 2.6.12-386 or i386, they installed fine, but I can't seem to find an interface to connect to the internet via Dial-Up, and enter my isp, and login details.

If someone could help me again, I'd appreciate it, before this thread gets bumped way down to the bottom again, Thank You:)

---

### Post by elamericano on 2006-05-12
easyubuntu and automatix can help you set up DMA, without doing an expert install.

I don't know why that means sudo doesn't work, but isn't your syntax wrong there?

su -c <command>

---

### Post by steve.horsley on 2006-05-12
If you do a normal install, the user you give at install time is added to the **admin** group. Mambers of the admin group are allowed to use sudo. My /etc/group file contains this line:
admin:x:112:steve
Perhaps you can fix this by editing your /etc/group file (as root of course). 
If that doesn't work, I'm out of ideas.

---

### Post by jrib on 2006-05-12
expert install won't create the admin group nor will it setup the sudoers file for you, here's a one liner to take care of that as well as add your user to the admin group (replace your username where it says your_normal_username)

```

addgroup --system admin; echo "%admin ALL=(ALL) ALL" >> /etc/sudoers && adduser your_normal_username admin

```

as root of course

---

