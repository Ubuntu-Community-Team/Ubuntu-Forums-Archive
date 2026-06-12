---
title: "Nautilus Crash when accessing NTFS portition"
date: 2010-02-08
forum: General Help
---

### Post by JarekG on 2010-02-08
I currently have 3 drives. 1 is running nothing more than Ubuntu, 2 drives are NTFS drives that I have from Windows days...I need them that way case they are big and at some point I may need to go back to windows (don't want to though).
About 3 days ago I was un-raring some files on my big portition (500 G...the files were about 24 rar files with total after extract +/- 600 megs)

I also had FireFox open and I was checking email....something happen and my computer become unresponsive...no mouse, no keyboard.
So I flip the switch (after about 5 minutes waiting).
I can start Ubuntu not a problem but as soon as i try to mount my drive that was mounted at the time of "re-boot" nautilus is crashing, my desktop is gone.
I can see the file on that drive in terminal, I can view/modify some of the files...I can see and work with the files using GNOME Commander.
I try testdisk, fsck, ntfsfix and I also try XP chkdsk (that one took long to run).

Now does any one know how to fix this? If i can fix this I can move some of the file to other drives and maybe format that drive to ext3.
This drive also has my VMPlayer XP files so I do need that (not able to connect to Sonic Wall VPN with x64 linux so need to use XP).

When I run after the restart Disk Utility it told me that the drive had some problems, now when I run it it's saying all is nice and no problems.

Any help would be appreciated.

---

### Post by JarekG on 2010-02-09
Anyone?

---

### Post by warfacegod on 2010-02-09
Use the extended selftest of:

```
sudo apt-get install gsmartcontrol
```

It should take around 30 minutes or so. Although my gut tells me that this isn't a hardware issue at all but a Nautilus problem or possibly fstab or permissions issue.

---

### Post by Mark Phelps on 2010-02-09
Couldn't tell from what you wrote ... but were you unraring the file to the NTFS partition?  IF so, when you rebooted your machine, the NTFS filesystem automatically set the "dirty bit" -- which will now prevent Ubuntu from mounting it cleanly.

You will need to go into MS Windows and run chkdsk on the partition(s) that were open when you shutdown the machine.

---

### Post by warfacegod on 2010-02-09
> **Mark Phelps said:**
> Couldn't tell from what you wrote ... but were you unraring the file to the NTFS partition?  IF so, when you rebooted your machine, the NTFS filesystem automatically set the "dirty bit" -- which will now prevent Ubuntu from mounting it cleanly.

You will need to go into MS Windows and run chkdsk on the partition(s) that were open when you shutdown the machine.

It looks like he already used chkdsk.

Perhaps plugging it into Windows and then Safely Remove Hardware will do the trick.

---

### Post by JarekG on 2010-02-09
Thanks, the one thing that I have not try is using gsmartcontrol

I will try it as soon as I get home. Since I can access the drive for backup I may just backup my stuff ant create one big ext3 drive.

---

### Post by JarekG on 2010-02-09
I think warfacegod is on to something with the permission issue.
I did sudo nautilus and I was able to access the drive with out problems.

Now the question is how do I fix it?
I did run gsmartcontrol and it did say it was all good.

---

### Post by warfacegod on 2010-02-09
> **JarekG said:**
> I think warfacegod is on to something with the permission issue.
I did sudo nautilus and I was able to access the drive with out problems.

Now the question is how do I fix it?
I did run gsmartcontrol and it did say it was all good.

I think I'm gong to ask the staff to send an automatic email to all new users on this because I've been seeing it allot recently. Using sudo for any GUI app is dangerous, especially nautilus. It can cause file and filesystem corruption. Please use gksudo instead, much safer. (Errgh! Third time today!](*,):biggrin:)

That being said, I have no idea how to deal with permissions on an NTFS drive. Frankly, I liked your idea of making an ext3 drive. Although, I'd use ext4.

---

### Post by warfacegod on 2010-02-09
By the way, if gsmart says your drive is okay then you can probably stake your life on it.

---

### Post by JarekG on 2010-02-09
I don't use sudo all the time, in fact this is first time I did use with nautilus, just to test it. 
I didn't do any work, I just want to see if it's gone crash after you mention the permission issues.
As for ext4, I read in some places that it's not as stable as ext3...this is why when I installed Ubuntu I used ext3.


> **warfacegod said:**
> I think I'm gong to ask the staff to send an automatic email to all new users on this because I've been seeing it allot recently. Using sudo for any GUI app is dangerous, especially nautilus. It can cause file and filesystem corruption. Please use gksudo instead, much safer. (Errgh! Third time today!](*,):biggrin:)

That being said, I have no idea how to deal with permissions on an NTFS drive. Frankly, I liked your idea of making an ext3 drive. Although, I'd use ext4.

---

### Post by warfacegod on 2010-02-09
I've been using ext4 since 9.04 and I've never had an issue with it. By the way, did you try my suggestion in post #5?

---

### Post by JarekG on 2010-02-10
No i have not, I don't have any Windows Machines to put it in and I don't want to install windows just for that. I work with windows for 10 hours a day so in my free time I want to enjoy my computer experience :p .

I can get the files by either terminal or using Gnome Commander so I'm OK for now and this weekend I may just go get external drive so I can make a backup of that drive and format that drive.

Do you know how would Ubuntu react if I format this drive ext4 (having the main system as ext3)?


> **warfacegod said:**
> I've been using ext4 since 9.04 and I've never had an issue with it. By the way, did you try my suggestion in post #5?

---

### Post by warfacegod on 2010-02-10
> Do you know how would Ubuntu react if I format this drive ext4 (having the main system as ext3)?

It'll be a bit faster. Aside from that Ubuntu won't care in the least.

---

### Post by JarekG on 2010-02-15
So I have a question. I formatted the drive to be ext4 but now I'm not able to use it. 
How do I make it my drive so I can use it. I can mount it but creating any files I get Permission denied.
I used GParted to delete the NTFS partition and create new ext4.
And is there a way I can mount the drive when my computer starts.

> **warfacegod said:**
> It'll be a bit faster. Aside from that Ubuntu won't care in the least.

---

### Post by warfacegod on 2010-02-15
```
sudo chown -R username:usergroup /media/drivename
```

This will make you the owner. Username and group should be your username. Mount the drive and look in the /media folder for drive name. If you didn't give it a label during formatting, then the name should be a long series of numbers and letters.

---

### Post by JarekG on 2010-02-15
That did the trick, thank you for that.
Is there a way I can mount the share when Ubuntu starts?

---

### Post by warfacegod on 2010-02-15
This might help:

[http://ubuntuforums.org/showthread.php?t=1304192&highlight=automount]("http://ubuntuforums.org/showthread.php?t=1304192&highlight=automount")

If not, post back and I'll PM someone that knows more about that than I do.

---

### Post by JarekG on 2010-02-17
Thanks for your help.
I did use [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive") as a guide and appears to be working very well.
This has been for sure very interesting road for me. But I do like tinkering with 'computer stuff' so it was fun. This is my 4th time trying Ubuntu but I think this time I'm gone stick with it for a while. 

I have VMPlayer install with image of XP just in case I need it (I'm windows application developer so sometimes I need this thing to do work stuff...but trying to get my head around C/C++ programming ;) ).

Thanks again for your help and people like you make using Linux enjoyable.


> **warfacegod said:**
> This might help:

[http://ubuntuforums.org/showthread.php?t=1304192&highlight=automount]("http://ubuntuforums.org/showthread.php?t=1304192&highlight=automount")

If not, post back and I'll PM someone that knows more about that than I do.

---

### Post by warfacegod on 2010-02-17
Glad to help. If there's anything else I can do, send me a PM.

---

### Post by amsterdamharu on 2010-02-18
```
So I flip the switch (after about 5 minutes waiting).
```

You should only switch off your computer like that as a last resort, especially when you have mounted NTFS because it'll dirty unmount. 
If your computer gets stuck you should first try:
control + alt + backspace
This will kick gnome and restart gdm (the graphic login screen) you probably loose any unsaved data.
control + alt + F1
If previous option did not work, This will get you into a console login on TTY1 (there are 7 of them and F7 is the gui). Log in as user and type 
```
sudo init 0
```
This will turn off your machine after it will try to unmount and shutdown programs safely.

---

### Post by JarekG on 2010-02-27
Thanks for the replay but I did try all of them and none of them work.
So flip the switch was the only thing that I could do...



> **amsterdamharu said:**
> ```
So I flip the switch (after about 5 minutes waiting).
```

You should only switch off your computer like that as a last resort, especially when you have mounted NTFS because it'll dirty unmount. 
If your computer gets stuck you should first try:
control + alt + backspace
This will kick gnome and restart gdm (the graphic login screen) you probably loose any unsaved data.
control + alt + F1
If previous option did not work, This will get you into a console login on TTY1 (there are 7 of them and F7 is the gui). Log in as user and type 
```
sudo init 0
```
This will turn off your machine after it will try to unmount and shutdown programs safely.

---

