---
title: "Formatting hard drives using the disk manager"
date: 2006-05-09
forum: General Help
---

### Post by GhandiBurger on 2006-05-09
I am currently have 2 hard drives, one with Ubuntu and the other with XP. I want to format my XP one to use with ubuntu as a second harddrive. When doing that, should I use extended 2 or extended 3 or fat 32 (just in case I install windows again)? and what should I make the access path or does it not matter?

---

### Post by Herman on 2006-05-09
I would use ext3. 
Ext3  is more modern than ext2, and features journalling, so it's more stable.
Fat32 is good if you need it to be able to be read and written to by both Windows and Linux, but it has a file-size limit of I think something like 4 GB, so if you have a large file like a DVD image or something like that fat32 might not do it.
There are Windows drivers now that can read ext3 I have read, but I haven't tried them myself.
To mount your ext3 data drive, you basically make a folder in /media and name it whatever you want, maybe 'data_drive' or something. ```
sudo mkdir /media/data_drive
```
Then you ammend your file called /etc/fstab by adding a line of typing describing your new drive and how you want your operating system to handle it.
You might do something similar to what I have described in [this link]("http://www.users.bigpond.net.au/hermanzone/p10.htm#automntlinx")under the heading '**Auto-mount  Linux data partitions on boot-up with read/write permissions'. **You will need to use the command 'sudo fdisk -l' to find out what to type in place of '/dev/hda6'. For yours it might be /dev/hdb1 for example.
There might be more information that you might find interesting further up that web-page too. if you need any specific help after that, just post here again and ask. :D Regards, Herman.

---

### Post by GhandiBurger on 2006-05-12
And this will automatically format it and wipe it clean right?

---

### Post by GhandiBurger on 2006-05-12
I used the disk manager to format it, but I cannot write to it. Any help with this?

---

### Post by GhandiBurger on 2006-05-12
Also, fstab is not editable. Any help Herman?

---

### Post by Herman on 2006-05-13
> And this will automatically format it and wipe it clean right? Yes, formatting always wipes (erases) the filesystem off any disk or partition that you choose to format, and then makes a brand new, clean filesystem for you.
    > I used the disk manager to format it, but I cannot write to it. Any help with this?'Disk Manager'?    What is 'Disk Manager?'
I recommend using Linux partitioners like the one on the Ubuntu install disk or the latest Gparted LiveCD, which is free. It's only a 25 or 30 mb download, you can get the .iso for it by clicking my right-hand 'signature link' and finding it. Otherwise maybe QTParted or GParted on a Knoppix or Ubuntu live CD are okay.

Edit: It might not matter what partitioner you used, if it will become writable after you edit /etc/fstab, try that first anyway. If that doesn't work then maybe try a different partitioner.

> Also, fstab is not editable.Maybe you have not opened the file by the correct Linux method?  To open the file so that it can be edited, you must use a 'sudo' command from your 'terminal' to open the file.
Try this to make a back up copy of the file before you edit it (just in case): ```
~$ sudo cp /etc/fstab /etc/fstab_backup
``` You can expect to be asked for your password to prove you are the authorized user. 
Then, to open it with the ability to edit it:
```
~$ sudo gedit /etc/fstab
``` 
Now you should be able to edit the file.
Good luck with it, regards, Herman :-D

---

### Post by GhandiBurger on 2006-05-13
Thank you for your patience Herman. However, I have one last problem. I did everything you said, but the disk is still not writeable. I have no idea why and have checked everythign and it is all exactly as it should be. I cannot thank you enough for this one last bit of help.

---

### Post by Herman on 2006-05-13
Let's have a look and check who owns the folder you are opening to get to that disk then, and what the file permissions are. Try this code in your terminal, and see what feedback you get:  ```
~$ ls -l /media
``` The expected reply for that command will be a vertical list of several folders inside you media folder. There will be a string of ten letters in the first column of each line designating file permissions.
In my computer for example,  I have one directory called 'hda2', but yours might be called 'hdb1' maybe,  (just as a guess).
The line I have for hda2 (for example) looks like this: 
> drwxr-xr-x   23   root   root   720   2006-04-29   23:30   hda2 Could your file ownership be inappropriate perhaps? We can fix that with a chmod command if that's what the problem is. Below is an example of a chmod command similar to what you might use. 
(assuming your directory in question is named 'hdb1', if not, replace with the actual name of your directory to be chowned, for example 'data_drive' was suggested earlier too.):
```
~$ sudo chmod -R 777 /media/hdb1
``` Try that and see if that fixes it, good luck, and  thank you also, for your patience too, GhandiBurger. Regards, Herman :-D

---

### Post by GhandiBurger on 2006-05-13
Thank a lot Herman. That fixed everything. Can't thank you enough. My next task is to install my graphics drivers. mwuahaha. I had figured out how to do that when it said I was missing some file...I dunno...I have an email in to nVidia. Oh well, it works, I just want a bigger resolution and can't get it. Thanks again.

---

### Post by Herman on 2006-05-13
Thanks you for the feedback , GhandiBurger, I'm happy now too! :D 

I don't know about graphics and video hardware/software though. If you need help with that you should start a new thread with a heading that will attract the interest of someone who knows much more than I do on that subject.

All the best with everything! Regards, Herman :D

---

