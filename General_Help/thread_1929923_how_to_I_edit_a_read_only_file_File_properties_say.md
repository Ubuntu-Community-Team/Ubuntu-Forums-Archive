---
title: "how to I edit a read only file? File properties say read and write."
date: 2012-02-22
forum: General Help
---

### Post by needhelplinux on 2012-02-22
I am using lubuntu that I installed from ubuntu 11.04, but all I installed was "lubuntu-core", not the full version. I can switch back into ubuntu if I need to. I think it will use gnome since my computer's not fast enough for unity.

I am trying to set up ntp servers using this topic: [http://ubuntuforums.org/showthread.php?t=862620](http://ubuntuforums.org/showthread.php?t=862620)

I am trying to edit the file ntp.conf, but it won't let me and it says read only at the title bar. If I check properties and check permissions, it says read and write, so why isn't it working? The group says root, but if I try and type something else there, it won't let me.

I don't know how to use sudo and I can't find anything on google to make it work. What do I type in the terminal? Just "sudo" doesn't give me that right. I don't know how to use chmod and I can't find anything with google. I just type "chmod filename"? I don't know what something like "---r----r" means.

---

### Post by gennatolls on 2012-02-22
try:
gksudo gedit /path/to/ntp.conf

good luck

---

### Post by 3rdalbum on 2012-02-22
Anything outside your home directory is a system file and can only be edited by root.

I am not familiar with Lubuntu so I can't give you the absolute easiest instructions, but you can either run the text editor as root, or the whole file manager and then just double click the file.

In the terminal, type:

sudo nano (then the full location and name of the file)

You will be asked for your password. Type it and hit Enter. there will be no feedback as you type.

Now you have run a simple text editor as root and made it open the file you want to edit.

---

### Post by IWantFroyo on 2012-02-22
Open Terminal.

```
gksudo gedit /etc/ntp.conf
```

Type in your password, and you'll be good to go. Just be careful. I'd recommend making a backup file before you edit anything, just so you feel more comfortable.

```
sudo cp /etc/ntp.conf ~/.
```
This will make a backup in your home directory. Trash when finished.

---

### Post by needhelplinux on 2012-08-09
I apologize for the late reply. I tried the following code to edit "read-only" files and it worked:

```
gksudo gedit /path/to/ntp.conf
```

Thank you all for answering.

---

