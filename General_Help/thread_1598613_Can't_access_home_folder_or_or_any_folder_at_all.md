---
title: "Can't access home folder or or any folder at all"
date: 2010-10-16
forum: General Help
---

### Post by jvhellraiser on 2010-10-16
hi guys i had everything working just fine i restart and for my surprise i couldn't open my home folder or any other folder at all
plaese HELLLLLLPPPPP!!!!

---

### Post by oldfred on 2010-10-16
My first guess is fstab. Did you edit it and not check it with a mount -a? If it is corrupted it may not let you mount folders. 

Did you get any error messages on boot? Check logs and/or reboot without quiet splash or using recovery mode.

---

### Post by jvhellraiser on 2010-10-16
nop no errors at all it just look like is loading and then it wont open and no i haven't touch anything cause i don't know to much about ubuntu and i don't want to mess it up.so no reason why is not working and i don't no how terminal things work so iam comfuse.

---

### Post by oldfred on 2010-10-16
Look in system, administration, log file viewer
Check messages & syslog. They are large but you are just looking for errors.

---

### Post by jvhellraiser on 2010-10-16
i have no idea:( this is big!!

maybe this one?

jvhellraiser-desktop kernel: [   97.221478] gnome-panel[1375]: segfault at 4 ip 080ad2f9 sp bfda1e30 error 4 in gnome-panel[8048000+83000]

:(:(:(:(

---

### Post by VMC on 2010-10-16
> **jvhellraiser said:**
> hi guys i had everything working just fine i restart and for my surprise i couldn't open my home folder or any other folder at all
plaese HELLLLLLPPPPP!!!!

Do you get a Desktop? If so can you open the Terminal. Try this, Alt+F2, then tick the Run in Terminal, then type *bash*. If the Terminal comes up, type the following:

```
pwd
ls -ld
```

---

### Post by jvhellraiser on 2010-10-16
i get this with that cause i can open the terninal is only  the folders that iam having problems.

drwxr-xr-x 49 jvhellraiser jvhellraiser 4096 2010-10-16 22:28

---

### Post by VMC on 2010-10-16
> **jvhellraiser said:**
> i get this with that cause i can open the terninal is only  the folders that iam having problems.

drwxr-xr-x 49 jvhellraiser jvhellraiser 4096 2010-10-16 22:28

See if you can open your folders using the terminal.
For example, "ls Desktop", or "cd Desktop". If you can maybe gnome settings are messed up.

---

### Post by jvhellraiser on 2010-10-16
i get this but how do you open your home folder?

jvhellraiser@jvhellraiser-desktop:~$ cd Desktop
jvhellraiser@jvhellraiser-desktop:~/Desktop$

---

### Post by mc4man on 2010-10-16
Do you have any folders on your desktop? If not then create one (r.click -> create folder

Then give this a try - 
r. click on the folder -> Open With -> Other application, scroll down a bit, choose 'Open folder' and click 'Open'. Then try opening your home folder again

---

### Post by VMC on 2010-10-17
> **jvhellraiser said:**
> i get this but how do you open your home folder?

jvhellraiser@jvhellraiser-desktop:~$ cd Desktop
jvhellraiser@jvhellraiser-desktop:~/Desktop$

You are in your home folder. What is happening is Nautilus can't open your folders. If you do a "ls -la" from the terminal you opened up, you will see your ~/home folder files and directories.

edit: It was mentioned about your */etc/fstab* file. Can you cat that out and paste it here. Also, are you running a separate partition for your "/home"?

---

### Post by jvhellraiser on 2010-10-17
i get this O.o?

jvhellraiser@jvhellraiser-desktop:~$ /etc/fstab file
bash: /etc/fstab: Permission denied
jvhellraiser@jvhellraiser-desktop:~$ sudo su
root@jvhellraiser-desktop:/home/jvhellraiser# /etc/fstab file
bash: /etc/fstab: Permission denied
root@jvhellraiser-desktop:/home/jvhellraiser#

so how do you open fstab file anyway?

---

### Post by VMC on 2010-10-17
> **jvhellraiser said:**
> i get this O.o?

jvhellraiser@jvhellraiser-desktop:~$ /etc/fstab file
bash: /etc/fstab: Permission denied
jvhellraiser@jvhellraiser-desktop:~$ sudo su
root@jvhellraiser-desktop:/home/jvhellraiser# /etc/fstab file
bash: /etc/fstab: Permission denied
root@jvhellraiser-desktop:/home/jvhellraiser#

so how do you open fstab file anyway?

From that terminal type this:
```
$ cat /etc/fstab
```

---

### Post by oldfred on 2010-10-17
From the terminal type this:

```
sudo mount -a
```

If it comes back to the terminal without messages, it says fstab is ok, if you get messages it will be what entry in fstab is in error. Post those also.

---

