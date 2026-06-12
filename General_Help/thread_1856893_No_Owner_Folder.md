---
title: "No Owner Folder"
date: 2011-10-09
forum: General Help
---

### Post by pracrichard on 2011-10-09
Hi,I have somehow manged to create a folder with files in it, located in my the public folder under documents, which has 'nobody' as the owner. The files all open and can be read but I cannot delete them.

These files are rather sensitive, I was creating a private user for them at the time. I now urgently need to remove them.

Can anybody help please?

I have attached a screenshot.

Many thanks

Richard Jannaway (pracrichard)

---

### Post by matt_symes on 2011-10-09
Hi

Press alt + f2 together to bring up the run application dialog.

Enter

```
gksudo nautilus
```to open Nautilus with root privileges. Enter your password. 

**Be very careful now as you can delete any files on your system.**

Navigate to the correct directory and delete the files you want to then close Nautilus right away.

Kind regards

---

### Post by coffeecat on 2011-10-09
I'm guessing that samba sharing came into this somewhere and that the files belong to the "nogroup" group.

There are two ways of dealing with this both involving the terminal. I'm not sure exactly what you mean by "public folder under documents", because Public and Documents are two separate default folders in your home folder, but assuming the files are in your ~/Public folder, you could:

```
sudo rm ~/Public/*
```

Caution - that will remove everything in ~/Public. ("~/" is shorthand for your home folder.) And if you have sub-folders within Public also containing files you wish to remove, it gets more complicated.

The alternative is to:

```
sudo chown -R yourusername: ~/Public/*
```

Substitute your account name for "yourusername" and don't omit the trailing colon. That will re-own all files in all subdirectories within Public and you will be able to delete them with the GUI.

A third option is to use a root nautilus to delete things, but if you are not careful, the "deleted" files will simply end up in root's trash.

One other point: if you want to completely delete the files beyond reach of data recovery software, you need to shred them first. Post back in you need help with this.

And one last point: you posted a Gimp image file. If you want to post a screenshot, it is more convenient to use the default png file.

---

### Post by matt_symes on 2011-10-09
Hi

There are some very good points by coffeecat, especially this thoughts on samba. He is more thorougher than i am.

I just wanted to add that if they are local files, not on a samba share, have you considered storing them in an encrypted folder on your hard drive using Cryptkeeper or some such.

It would add that extra layer of security while keeping ease of use.

Kind regards

---

### Post by pracrichard on 2011-10-09
> **matt_symes said:**
> Hi

Press alt + f2 together to bring up the run application dialog.

Enter

```
gksudo nautilus
```to open Nautilus with root privileges. Enter your password. 

**Be very careful now as you can delete any files on your system.**

Navigate to the correct directory and delete the files you want to then close Nautilus right away.

Kind regards
Many thanks for your terrific fast responses.** mat_symes** instructions were simple and worked perfectly. 

Whilst  was waiting I tried to use terminal to remove the directory but still got a failure.

---

### Post by pracrichard on 2011-10-09
> **matt_symes said:**
> Hi

There are some very good points by coffeecat, especially this thoughts on samba. He is more thorougher than i am.

I just wanted to add that if they are local files, not on a samba share, have you considered storing them in an encrypted folder on your hard drive using Cryptkeeper or some such.

It would add that extra layer of security while keeping ease of use.

Kind regards
Many thanks for the tip. I will investigate Cryptkeeper

---

### Post by coffeecat on 2011-10-09
@pracrichard, when you deleted the files with a 'gksudo nautilus' file browser, did you use the delete key alone, or did you use the shift-delete combination? If you used the delete key alone, open a 'gksudo nautilus' file browser again. It should open in root's home (/home). Press ctrl-H to show hidden files and open the .local folder. Now open the share folder and you should see a Trash folder. Have a look in there and in all the sub-folders in Trash to make sure your deleted files are not simply sitting in root's Trash.

---

### Post by matt_symes on 2011-10-09
Hi

> Many thanks for the tip. I will investigate CryptkeeperI use it myself for things like bank details and other important documents.

In Lucid it's very simple. When installed you get a panel applet that allows you to create a folder that is encrypted by entering a password to decrypt the folder.

When you want to view the folder you use the same panel applet to enter the same password to unencrypt the folder to open it in Nautilus.

A coffeecat highlighted make sure you did not move the files to roots trash but deleted them.

Kind regards

---

