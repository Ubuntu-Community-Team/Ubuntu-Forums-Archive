---
title: "Forgotten Root Password (Ubuntu 9.10)"
date: 2010-04-22
forum: General Help
---

### Post by Spades_Neil on 2010-04-22
I seem to have forgotten the password to my Linux. It's been out of use for some time now because I've gotten my new computer. However, I still have files on the old computer I want to gather up onto my shiny new terabyte hard drive.

Problem is... I can't log in. And I can't reset the password. I'd like to know how, but I'm having no luck. The Live CD has given me no luck either.

I'm wondering if there's a way to manually create a new user with admin powers and just go from there. I can't log into root or the one user that is on the computer right now.

---

### Post by bcbc on 2010-04-22
the root user doesn't have a password (usually). Use 'sudo' to elevate your own privileges to root, by supplying your own password.

If you've forgotten your own password, you can boot in recovery mode and drop to a root shell, and then change it there: hold down SHIFT while booting to ensure you get the grub menu, select recovery mode, when it boots select the last option (I believe) root shell. Then change your password: ```
passwd -change your_user_name new_password
```

Edit: if you upgraded to 9.10 from 9.04 and are using legacy grub, you have to press ESC instead of SHIFT to get the grub menu.

---

### Post by Spades_Neil on 2010-04-22
I'm at a "Recovery Menu" but when I choose the option to "Drop to a root shell" I have to enter a password anyway. :\

I got out of that and now I'm -at- something that says "Grub" but your command line doesn't work. I think it's because I gave you the wrong version of Ubuntu.

I'm doing something wrong here.

---

### Post by bcbc on 2010-04-22
> **Spades_Neil said:**
> I'm at a "Recovery Menu" but when I choose the option to "Drop to a root shell" I have to enter a password anyway. :\

You must have set the root password then.

I am not sure how you would get past that, other than booting from a live CD and then copying the data you need.

---

### Post by Spades_Neil on 2010-04-22
> **bcbc said:**
> You must have set the root password then.

I am not sure how you would get past that, other than booting from a live CD and then copying the data you need.

Looks like I'll have to dig it out, then. In which case how do I override the file protection? Btw, it's a 9.04 CD.

---

### Post by bcbc on 2010-04-22
> **Spades_Neil said:**
> In which case how do I override the file protection?

Are you referring to file encryption or user rights? If it's the former, I have no idea. You shouldn't have any problem if it's the latter.

---

### Post by Spades_Neil on 2010-04-22
> **bcbc said:**
> Are you referring to file encryption or user rights? If it's the former, I have no idea. You shouldn't have any problem if it's the latter.

Well I can't access half the files with the Live CD. Also I'm trying to figure out how to share a folder with the network so I can get into it with my computer...

Damn it, there's *gotta* be a way to reset the password. -.- Is there any way to create a new user without reinstalling? Because then I can just sudo everything.

---

### Post by bcbc on 2010-04-22
> **Spades_Neil said:**
> Is there any way to create a new user without reinstalling? Because then I can just sudo everything.
You need to sudo to create a new user. 

It sounds like you encrypted you home directory - I haven't done that myself but figure even the root password won't give you access. Encryption is a double-edged sword.

Now's about the time to learn about password cracking - and just hope you picked a weak password.

---

### Post by Spades_Neil on 2010-04-22
> **bcbc said:**
> You need to sudo to create a new user. 

It sounds like you encrypted you home directory - I haven't done that myself but figure even the root password won't give you access. Encryption is a double-edged sword.

Now's about the time to learn about password cracking - and just hope you picked a weak password.

If I have, then it was completely unintentional... I highly doubt that I encrypted my home directory. I've tried encrypting files before but I've never figured it out. I haven't ever attempted such a thing on my home directory.

---

### Post by bodhi.zazen on 2010-04-22
Boot a live CD.

Mount your file system, assuming Ubuntu is on /dev/sda1 ...

mount /dev/sda1 /mnt
sudo chroot /mnt /bin/bash

passwd # This sets the root password.

ls /home # list of users

passwd user_name_to_set # Sets users password

Reboot.

If you are using encryption , that will make it more complicated, and we would then need to know if it is LUKS or ecryptfs.

More likely then not, if you forgot your password for encrypted data, you will be out of luck.

---

### Post by bcbc on 2010-04-22
When you say "You can't access half the files with the live CD" do you mean you can't see them, or you're unable to open/copy them?

If the latter, try opening nautilus as root from a terminal:
```
gksudo nautilus
```

---

### Post by Spades_Neil on 2010-04-22
> **bodhi.zazen said:**
> Boot a live CD.

Mount your file system, assuming Ubuntu is on /dev/sda1 ...

mount /dev/sda1 /mnt
sudo chroot /mnt /bin/bash

passwd # This sets the root password.

ls /home # list of users

passwd user_name_to_set # Sets users password

Reboot.

If you are using encryption , that will make it more complicated, and we would then need to know if it is LUKS or ecryptfs.

More likely then not, if you forgot your password for encrypted data, you will be out of luck.

Forgive me, I'm a bit of an idiot when it comes to Linux. >_x I have little clue what any of this means.

Also, just in case, because I have this sort of luck, let's say Ubuntu *isn't* on /dev/sda1, how do I figure out where it is?

---

### Post by bodhi.zazen on 2010-04-22
> **Spades_Neil said:**
> Also, just in case, because I have this sort of luck, let's say Ubuntu *isn't* on /dev/sda1, how do I figure out where it is?

Boot the live CD and either fire up gparted or enter

fdisk -l

=)

---

