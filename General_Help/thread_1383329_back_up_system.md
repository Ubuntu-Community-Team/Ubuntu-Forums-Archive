---
title: "back up system"
date: 2010-01-17
forum: General Help
---

### Post by evelin on 2010-01-17
hello, i have read that i can backup the entire system with the home folder with commands, or with programs, such as clonezilla, but it doesnt work, so im trying to back it up with commands now but i cant find a good tutorial to explain what commands to use. does someone knows how to do this or where do i find  a good tutorial.

---

### Post by labinnsw on 2010-01-24
[ATTACH]144765[/ATTACH]

Here are the commands I use. You can modify to fit your requirements.
I also find all the other back-up/restore options inferior.
[URL="https://help.ubuntu.com/community/BackupYourSystem/TAR"]
A detailed explanation can be found here[/URL]

---

### Post by juky on 2010-01-24
> **evelin said:**
> hello, i have read that i can backup the entire system with the home folder with commands, or with programs, such as clonezilla, but it doesnt work, so im trying to back it up with commands now but i cant find a good tutorial to explain what commands to use. does someone knows how to do this or where do i find  a good tutorial.

Hi,

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

is a good one. I did it like that, except, I've added /media to exclusion part.

Cheers,
juky

---

### Post by labinnsw on 2010-01-24
> **juky said:**
> Hi,

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

is a good one. I did it like that, except, I've added /media to exclusion part.

Cheers,
juky


I could not remember where I got mine from. This looks like it. I will add a note to the top of my file for future reference.

---

### Post by Thomas Garman on 2010-01-24
When I tried this I got an error message saying '--exclude/lost+found' was not a valid command or recognized or some such and that I should review 'tar --usage'.  So, I simply omitted '--exclude/lost+found'.  Trying again I got the message again but this time the culprit was '--exclude/mnt'.  So I ommitted this exclusion as well.  Then I tried running it again and I was told that I had no permission...  very frustrating.

So I appended sudo and tried again...  now it is actually "working" in the sense that it seems to be copying all of my files/folders.

But is it really working?  and why did it say '--exclude/mnt' was not valid?

Is there not some simple backup tool that will allow one to make a backup of Ubuntu as it is configured?

The whole reason I got started down this path was that it has literally taken me months to get the point where my Ubuntu system will play a dvd and stream a video and open a virtual machine etc etc and now I want to save this configuration because if my hard drive got wiped out or something, then I don't want to spend several months trying to figure out how to get all of this to work again.

And yet, when I search for "backup Ubuntu" or anything similar all I run into are these weird methods described in the forums that might work.  Or maybe they don't.  Who really knows?

The last line in my terminal says:

tar: Exiting with failure status due to previous errors.

So very confidence inspiring. and then finally... where did it go?  I have searched in every conceivable directory and it either vanished or it was never created.

---

### Post by rnerwein on 2010-01-24
hi
just try your option --exclude /mnt ( must be a space following the option )
ciao

---

### Post by Thomas Garman on 2010-01-24
@renerwin  sorry, that was just the way I typed it in the reply above.  I actually put

--exclude=/mnt --exclude=/lost+found

when I typed it into the terminal.

Mainly the point is this:  I really don't have the slightest idea if this method really worked.  But thanks for your reply.

---

### Post by labinnsw on 2010-01-24
> **Thomas Garman said:**
> When I tried this I got an error message saying '--exclude/lost+found' was not a valid command or recognized or some such and that I should review 'tar --usage'.  So, I simply omitted '--exclude/lost+found'.  Trying again I got the message again but this time the culprit was '--exclude/mnt'.  So I ommitted this exclusion as well.  Then I tried running it again and I was told that I had no permission...  very frustrating.

So I appended sudo and tried again...  now it is actually "working" in the sense that it seems to be copying all of my files/folders.

But is it really working?  and why did it say '--exclude/mnt' was not valid?

Is there not some simple backup tool that will allow one to make a backup of Ubuntu as it is configured?

The whole reason I got started down this path was that it has literally taken me months to get the point where my Ubuntu system will play a dvd and stream a video and open a virtual machine etc etc and now I want to save this configuration because if my hard drive got wiped out or something, then I don't want to spend several months trying to figure out how to get all of this to work again.

And yet, when I search for "backup Ubuntu" or anything similar all I run into are these weird methods described in the forums that might work.  Or maybe they don't.  Who really knows?

The last line in my terminal says:

tar: Exiting with failure status due to previous errors.

So very confidence inspiring. and then finally... where did it go?  I have searched in every conceivable directory and it either vanished or it was never created.
You can ignore the error. I always get that last error but I have never had a problem restoring the files.

To check if it worked, find the backed up file, right click and select extract here. If the resulting file looks like your system, then you know that the back was successful.

I have not found anything that is as efficient and I have given up looking. I use this with a live Ubuntu CD even for Windows.

The first errors were due to your oversight. If you reread the instructions carefully, you will notice that the first thing to do was to change the user mode to root/super user.

The clue to where it went resides in the 2nd  command you should have executed. e.g. ```
cd /media/backup/Home
```Puts the file on another partition/drive called "backup" in a directory called "Home"

If you followed the link posted by juky, the file will be in the root directory. Before you do anything else, move it to another location.

[Some other back-up options can be found here.]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by evelin on 2010-01-29
> **labinnsw said:**
> [ATTACH]144765[/ATTACH]

Here are the commands I use. You can modify to fit your requirements.
I also find all the other back-up/restore options inferior.
[URL="https://help.ubuntu.com/community/BackupYourSystem/TAR"]
A detailed explanation can be found here[/URL]

hello, i have a problem i fomatted the disk now it change the uuid i think thats how it is called how can i remake the grub or repair this

---

### Post by labinnsw on 2010-01-29
> **evelin said:**
> hello, i have a problem i fomatted the disk now it change the uuid i think thats how it is called how can i remake the grub or repair thisTo follow these instructions, switch to root mode. Using a terminal type```
sudo su
``` To use a GUI, type the following code in a terminal.```
sudo nautilus
```

1. Reinstall Ubuntu.
2. From the new installation, save the directory "/boot/grub" and all its contents on another device (preferably external)
3. Also save the file "/etc/fstab" to anther device (preferably external)
4. Restore the old system.
5. Delete "/boot/grub/" and replace it with the new one that you saved.
6. Delete "/etc/fstab" and replace it with the new one that you saved.
7. Make directories in "/media/" to represent any devices that you would like to mount.

---

### Post by evelin on 2010-01-30
> **labinnsw said:**
> To follow these instructions, switch to root mode. Using a terminal type```
sudo su
``` To use a GUI, type the following code in a terminal.```
sudo nautilus
```

1. Reinstall Ubuntu.
2. From the new installation, save the directory "/boot/grub" and all its contents on another device (preferably external)
3. Also save the file "/etc/fstab" to anther device (preferably external)
4. Restore the old system.
5. Delete "/boot/grub/" and replace it with the new one that you saved.
6. Delete "/etc/fstab" and replace it with the new one that you saved.
7. Make directories in "/media/" to represent any devices that you would like to mount.

thanks it worked 
hey you said you can backup the hole disk of windows windows too with this method is it right?

---

### Post by labinnsw on 2010-01-30
> **evelin said:**
> hey you said you can backup the hole disk of windows windows too with this method is it right?

That is correct. Just treat the Windows partition as a directory.

---

