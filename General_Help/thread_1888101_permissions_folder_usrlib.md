---
title: "permissions folder /usr/lib/"
date: 2011-11-28
forum: General Help
---

### Post by ubto66 on 2011-11-28
Some files has to be moved to usr/lib/.
But ubuntu 10.04 says:
permissions -> owner: root folder access: create an delete files ->
you are not the owner so you cannot change these permissions.

How do you change permissions in order to move files to the folder?
Thanks.

---

### Post by nothingspecial on 2011-11-28
You do not change the permissions of system files.

You elevate your user to root using sudo

Typing ```
gksudo nautilus
``` in a terminal will allow you to move files to /usr/lib.

Are you sure you need to do this? What is your end goal.

Be very careful because nautilus as root will also allow you to delete /usr/lib (or anything else) and that would break your system.

---

### Post by ubto66 on 2011-11-28
Thank you for a fast answer.
 It's about installing a piece of software that adds
 a feature to Ubuntu. The software
 source is reliable. Apparently  the installation instructions are not specific enough
 

 Can you give specific instructions on how
 to move files from the desktop to the usr/lib/ folder?
 Thanks.

---

### Post by nothingspecial on 2011-11-28
Well, you would open a terminal and type

```
sudo mv files /usr/lib
```

Where files are the files you want to move there.

Like I said, this can go horribly wrong if you don't understand what you are doing.

Perhaps you could post what the files are and where they are?

---

### Post by ubto66 on 2011-11-29
You download a tar file. After extracting the tar file, instructions say, that
files placed in a subfolder must be moved to /usr/lib.
I now understand your concern because usr are the system files?
But moving the files to /usr/lib is the only way to install the feature.
The software also comes in a windows and a mac version.
The windows version is a exe file.

I managed to move the files from the extracted package to the /usr/lib folder.
I will notify if I get the software to run properly.

It seems this way to install software on ubuntu is not common?
Thanks.

---

