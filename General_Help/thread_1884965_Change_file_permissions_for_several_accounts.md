---
title: "Change file permissions for several accounts"
date: 2011-11-22
forum: General Help
---

### Post by jerrydelfine on 2011-11-22
Hello all. I was hoping someone could give me a bit of advice. 

I've recently had hardware problems with a laptop and have removed the hard disk from the computer and put it in an external hard drive carcass. 

There are three password-protected Ubuntu accounts that I'd like to access on the hard drive. Since the hard drive has now just become an external backup drive, I don't really see any point in keeping the password protection. 

The problem is now that the three accounts on the hard drive are not accessible from my main computer. The main computer (the one that works, also running Ubuntu) doesn't have permissions to access the files in each account, and since it is not the owner of the files, it also can't change the file permissions. 

My question is: what would be the best way to change the old permissions on all three accounts so that they are readable/writeable by the main computer?

I appreciate any suggestions! Thanks in advance.

---

### Post by WorMzy on 2011-11-22
Use chown as root, using sudo.

For example, if you've mounted the partition to /media/oldubuntu, then run this:

```
sudo chown -R $USER:$USER /media/oldubuntu/home/*
```

This will make every file and folder in the oldubuntu's home folder belong to you.

Be careful with "sudo chown" though, one mistake and you'll bork the entire operating system.

---

### Post by audiomick on 2011-11-22
if you want to do this using a graphical interface, you will need to start nautilus, the file manager, with root priviliges.
```
gksudo nautilus
```In the instance of nautilus that then starts, you will be able to right click on the user's folder and choose "properties". There, go to the permissions tab and change the owner to the user that you want to own it. There is a button down the bottom of the tab to make the ownership change apply to every file in the folder.

You should close the "root" instance of nautilus immediately when you have finished. You don't want to be doing anything in there that you are not thinking very carefully about. If you tell it to erase system files or something, it will.

---

