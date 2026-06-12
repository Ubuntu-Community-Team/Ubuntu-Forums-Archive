---
title: "Acess Problem! ROOT"
date: 2010-10-06
forum: General Help
---

### Post by serdar132 on 2010-10-06
The other day I had recovered a failed external hard drive running TestDisk. It worked out just fine. 
Only problem I have now, the files that I have recovered are shown as ROOT. And I need normal acess to there files to be able to write them.

Any idea how can I change that permission?

Thanks in advance
Serdar

---

### Post by endotherm on 2010-10-06
I'm assuming that you mean that they are now owned by root, or are you saying that they are all now named 'ROOT'? is this volume a system drive, or data?

unfortunately, you will need to know the permissions of the original files to set them back. 

just to clarify are you booted into the system when you see this ownership or are you working off a live CD boot? liveCD sessions often can't identify the real owner of files. 

it;s strange that testdisk would alter ownership/permissions. those are stored on the INODE, but as I understand it testdisk works mostly on the partition table, so the original inodes should have remained intact.

---

### Post by serdar132 on 2010-10-07
They are owned by Root, the&#305;r names are all normal. This external drive was my Ibook G4's hard drive, but I use it as an external disk.

I am not using Live CD, I an booted to the system

---

### Post by CharlesA on 2010-10-07
You can always just chown the files to get the owner and group set correctly.

---

### Post by 3rdalbum on 2010-10-07
> **CharlesA said:**
> You can always just chown the files to get the owner and group set correctly.

+1. If you don't understand what is meant by "chown", then go to the terminal and type:

```
man chown
```

to be told how to *chown* (Change Owner) of the files. You will need to run the chown command as root with *sudo*.

---

### Post by serdar132 on 2010-10-07
Thank you people. It jsut work great except one thin when I use the command : sudo chown serdarvural132 place of the file

It only changes the permissions of the folder not the files inside!
Is there any way to change automaticly the folder and the files inside?

thanks

---

### Post by Zill on 2010-10-07
"man chown" shows the -R option:
-R, --recursive
              operate on files and directories recursively

---

### Post by endotherm on 2010-10-07
ok, be very careful with this. i didn;t mention chown initially because it can be dangerous if you don't know exactly what you want to do with it.

to apply a chown command to every file and folder within a heirarchy, you add the '-R' option
```
sudo chown -R newowner:newownergroup pathtofiles
```

or if you just want to change the owner on files within a specific folder use this:

```
sudo chown newowner:newownergroup pathtofiles/*
```

---

