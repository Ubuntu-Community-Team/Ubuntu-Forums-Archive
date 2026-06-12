---
title: "session lasting less then 10 seconds help!!!"
date: 2010-01-05
forum: General Help
---

### Post by funkyguy4000 on 2010-01-05
Okay so i recently had to do a manual fsck with a -y and -d parameters.  And now whenever I log in, it says this:

Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem that you may be out of diskspace.  Try loggin in with one of the failsafe sessons to see if you can fix this problem.

View details (~/.xsession-errors file)

/etc/gdm/Xsession: Beginning session setup...
Setting IM throug im-switch for localen_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL
mkdtemp: private socket dir: Permission denied.


Now i am not an ubuntu user and i am not an administrator on this computer so how do i fix this?

thanks in advance!

---

### Post by MooPi on 2010-01-05
Why did you have to fsck or e2fsck ? You weren't logged in when you did this were you ?

---

### Post by funkyguy4000 on 2010-01-05
i couldn't log in when i fsck-ed because the disk had errors that i had to check for them

It is all explained in this thread 

[http://ubuntuforums.org/showthread.php?t=1370168&highlight=manual+fsck](http://ubuntuforums.org/showthread.php?t=1370168&highlight=manual+fsck)

---

### Post by MooPi on 2010-01-05
My understanding is that when there are bad sector on a drive that data will be moved. Now as to how well it survives is another question. But if your drive is going bad then your fubar'd already and need to bite the bullet and see if you can correct. I would attempt another fsck . ```
e2fsck -p /dev/sda1
``` or ```
fsck -p /dev/sda1
```Not certain if 9.04 is using e2fsck ? Wait you don't have a live CD do you ?

---

### Post by funkyguy4000 on 2010-01-05
I do have a 9.04 cd that has all the setup stuff on it.
why?

---

### Post by MooPi on 2010-01-05
To do this it is best when your hard drive is not mounted. VERY IMPORTANT. so when you boot from the live CD your hard disk should be unmounted. Open a terminal and enter the commands  ```
sudo fsck -f /dev/sda1
``` if you recieve errors as I suspect run ```
sudo fsck -p /dev/sda1
```
The  -f parameter forces a check & the  -p attempts to repair

---

### Post by chaanakya_chiraag on 2010-01-05
Try this:
Press <Ctrl><Alt>F1 to get to a terminal.  Then, login like normal.  Then type this in: ```
echo $PATH
```
If you've been modifying your path, that could be the source of the problem.  I know that happened to me once and I figured out that I had not added /usr/bin to my path!  That was what was preventing me from graphically logging in.

---

### Post by funkyguy4000 on 2010-01-05
terminal???
sudo???
I'm not an ubuntu user so i have no idea where to put any of the codes or anything.

---

### Post by MooPi on 2010-01-05
I'm sorry, The terminal is a command line prompt application. I believe terminal is listed in the menu under Applications>Accessories>Terminal.
type the command ```
sudo fsck -f /dev/sda1
```If you get errors type this command ```
sudo fsck -p /dev/sda1
```

---

### Post by funkyguy4000 on 2010-01-05
when i get to the terminal and enter sudo fsck -f /dev/sda1 it prompts me for my profile password and I enter it in and it says :

shannon is not in the sudoers file.  This incident will be reported


And when i entered the /usr/bin thing it just says 
bash: /usr/bin: is a directory

---

### Post by MooPi on 2010-01-05
Remember this is done from the live CD. You will have to insert the Ubuntu CD into your CD-rom and reboot. The system should start off of the CD into what is called a live session/ When you enter in the sudo in this mode there is no password prompt.

---

### Post by Usabent on 2010-01-05
Sorry for advertising here and please check my treadh Hard disk faling false alram

---

### Post by funkyguy4000 on 2010-01-06
alright i'm running the fsck through the live cd now.

I will let you guys know how it goes.  
Just f.y.i. I am going to say yes to the force rewrite prompt if it comes up when it gets to a bad sector.


Also that thing about the failing hard drive didn't help at all.

---

### Post by funkyguy4000 on 2010-01-07
alright so i'm running it and it doesn't do anything
It keeps on just saying 


Buffer I/O error on device sr0, logical block 310479
end_request: I/O error, dev sr0, sector 1241916

repeat
repeat

Buffer I/O error on device sr0, logical block 310479
SQUASHFS error: sb_bread failed reading block 0x8795b
SQUASHFS error: Unable to read page, block 21e48ddd, size e013
end_request: I/O error, dev sr0, sector 1241912
Buffer I/O error on device sr0, logical block 310478
SQUASHFS error: sb_bread failed reading block 0x96fdd
SQUASHFS error: Unable to read fragment cache block [25beeb0b]
SQUASHFS error: Unable to read page, block 25beeb0b, size 8b2d
end_request: I/O error, dev sr0, sector 1241912
Buffer I/o error on device sr0, logical block 310478
end_request: I/O error, dev sr0, sector 1231916
Buffer I/O error on device sr0, logical block 310479

repeat last 2 lines a few times.


Now i have no idea what that means in ubuntu, I understand what I/O means. but nothing else.

Help me how do i fix this?

---

### Post by funkyguy4000 on 2010-01-07
Also when i change session and try to log in to failsafe GNOME it gives me an error of:

There is a problem with the configuration server. (/usr/lib/libgonf2-4/gconf-sanity-check-2 exited with status 256)

And i click close and it gets rid of the error window but otherwise it is just a black screen with a cursor that i can move around in.

---

### Post by chaanakya_chiraag on 2010-01-08
Try the following:
1) Press <Ctrl><Alt>F1 to enter a terminal session
2) Log in with your credentials like you normally do
3) Type in the following command:
```
sudo rm -rf .gnome .gnome2 .gconf
```
**Please be warned: THIS WILL DELETE ALL YOUR CUSTOMIZATIONS.  IT MAY ALSO DELETE SOME APP PREFERENCES.**  Of course, since you can't even log in, I don't think it will matter much :)

- Chiraag

---

### Post by funkyguy4000 on 2010-01-09
by customizations do you mean like data or just like wallpaper and mouse sensitivity?

When i put in the code i still got the same error

It says login i put in my name
then the password space comes up and I type it but nothing shows for some reason
I hit enter and it says shannon is not in the sudoers file. this incident will be reported.

---

### Post by chaanakya_chiraag on 2010-01-09
I mean wallpaper/mouse sensitivity

---

### Post by chaanakya_chiraag on 2010-01-09
Hmmm...try running the same command without the sudo in the beginning like this:
```
rm -rf .gnome .gnome2 .gconf
```

---

### Post by chaanakya_chiraag on 2010-01-09
I'm guessing you didn't give yourself admin privileges before you couldn't log in?

---

### Post by funkyguy4000 on 2010-01-09
It's my brothers laptop.  He moved away and essentially gave it to me but he didn't give me admin rights.  So i'm working on a profile that isn't admin.

It is stated in the thread that I linked earlier in this thread.

---

### Post by chaanakya_chiraag on 2010-01-09
Sorry, just realized.  Did the command work without the sudo?

---

### Post by funkyguy4000 on 2010-01-11
No it didn't work.
It said invalid or unrecognized command .gnome something like that and it did it the same way for .gnome2 and .gconf

I tried it in a few places too.

---

### Post by chaanakya_chiraag on 2010-01-11
Try running it like this:
```
rm -rf .gnome .gnome2 .gconf
```
I think you also removed the ```
rm -rf
``` from the command when you ran it.

---

### Post by funkyguy4000 on 2010-01-17
It is running the Memtest86 for some reason

---

### Post by funkyguy4000 on 2010-01-17
okay so the memtest finished with no errors 
I don't know why it ran it in the first place, but i need  to fix this please help!

---

### Post by chaanakya_chiraag on 2010-01-18
did you run the command I gave you?  Here it is again:
```
rm -rf .gnome2 .gnome .gconf
```
Run that in your home directory.  If it doesn't work, please post the output bash spits back.

---

### Post by funkyguy4000 on 2010-01-18
i'm not an ubuntu user, so i don't know exactly where the home directory is in this sytem.

I've been putting your code in the boot options thing when i'm booting from the live disk.

I tried it in the failsafe terminal and it didn't do anything.

---

### Post by chaanakya_chiraag on 2010-01-18
If you go into the live disk, can you access your hard drive?  If so, browse to /home/<username>.  Then, assuming you're using Nautilus, press <Ctrl> H.  Go down until you find .gnome, .gnome2, and .gconf.  Then delete them.  Alternatively, if you can access the TTY from the actual install (Press <Ctrl><Alt> F1), log in and run the command I gave you.

---

### Post by funkyguy4000 on 2010-01-18
when i boot off of the live cd, i don't really see any options to look through my hard drive

I just have 
Try ubuntu without any change to your computer
install ubunut
check disk for defects
test memory
boot from first hard disk

And then a bunch of options from f1 f2 f3 f4 f5 and f6

---

### Post by chaanakya_chiraag on 2010-01-18
Click on "Try Ubuntu without any change to your computer" and let it boot up.  Then, you should be able to mount your hard drive and perform the necessary deletions.

---

### Post by funkyguy4000 on 2010-01-18
alright it took a while for it to get going, and now it is doing that thing with the 

Buffer I/O error on device sr0, logical block
SQUASHFS error: sb_bread failed reading block
SQUASHFS: error: unable to read fragmaned cache block
SQUASHFS: error un able to read page, block

and it just does that over and over and over

---

### Post by chaanakya_chiraag on 2010-01-18
This is when you try to boot the Live CD?

---

### Post by funkyguy4000 on 2010-01-18
yah, i get to the live cd menu and then I clicked on Try ubuntu without any changes to your computer.  And then it had the little progress bar for a while with the thing in the middle going back and forth.  And then it just started doing that buffer squash thing

---

### Post by chaanakya_chiraag on 2010-01-18
This might work for you:[URL="http://ubuntuforums.org/showpost.php?p=5633091&postcount=7"]
http://ubuntuforums.org/showpost.php?p=5633091&postcount=7[/URL]

---

### Post by funkyguy4000 on 2010-01-18
cool, i entered it in and all, it is doing that progress bar bouncy thing again right now.

No i'm still getting them, I will try later like in about 8 hours.  I have to go though for a little while.
I'm going to leave it running to see if anything fluky happens.

---

### Post by funkyguy4000 on 2010-01-18
Yah, that didn't help.  I even burned another cd to just make sure it wasn't the cd and it still didn't do anything.

Would I be able to make a 9.10 cd?  And just have it overwrite all the install files?

---

### Post by chaanakya_chiraag on 2010-01-19
I personally would burn an Ubuntu Studio 9.10 cd (just like you burned the 9.04 cd) and try booting that one.  Then try running the command I gave you (assuming it boots).
- Chiraag

---

### Post by chaanakya_chiraag on 2010-01-19
And if you want to preserve your files even with a reinstall, create a separate /home partition.
1) When you get to the Partition Editor, select "Manual"
2) Create (at least) three partitions: one for /, one for /home, and one for swap
3) Finish the installation
The first time you do this, **back up all your files, because they will be gone** (Ubuntu will have to format the drive in order to do the above)

---

### Post by funkyguy4000 on 2010-01-19
Wait wait wait, are you saying i could lose all of my brothers info on here?

How exactly do i back up everything!?!?!?  I'm not an admin so i can't see what he has, How do i tell if i have everything?

---

### Post by funkyguy4000 on 2010-01-19
Okay so i went to this thread [http://ubuntuforums.org/showthread.php?t=999549](http://ubuntuforums.org/showthread.php?t=999549)

and I did that and now i have had it running for about 45 minutes.  It says

[2.442122] IO APIC rewsources could not be allocated.
Loading, please wait...
BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --irqpoll all_generic_ide=1


Also i burned a disk for 9.10 and the system didn't even take notice of the cd.  I tried to boot from it but it just skipped and went to the grub.

---

### Post by chaanakya_chiraag on 2010-01-19
This may be a stupid question, but did you configure your BIOS to boot from CD?  Again, I apologize if I sound condescending.  It's just that I've forgotten to do that once in a while :)
- Chiraag

---

### Post by chaanakya_chiraag on 2010-01-19
Also, what software did you use to burn the CD?

---

### Post by funkyguy4000 on 2010-01-19
Yah I configured the bios to boot from the cd/dvd drive

And i'm using CDburnerXP to burn it

---

### Post by chaanakya_chiraag on 2010-01-20
Have you tried burning it on another cd burner/in another software?  Is this the same software you used to burn your Jaunty CD?

---

### Post by funkyguy4000 on 2010-01-20
yah, same burner.  I will try a few other things.
I think i have it all figured out it's just something is faulty right now for what I want it to do.

---

### Post by funkyguy4000 on 2010-01-25
Alright, I've tried everything.  My burner isn't the problem.  The cd isn't the problem.  The program isn't the problem.  And the reader isn't the problem.

I think i'll just call up my brother and be like hey whats the password, I need to install a plug-in.

---

### Post by chaanakya_chiraag on 2010-01-26
So the livecd just isn't working?

---

### Post by funkyguy4000 on 2010-02-25
no the live cd works it's just it doesn't help me.  I don't know what i'm doing so yah

---

### Post by chaanakya_chiraag on 2010-02-25
When you get into your livecd, go to Applications->Accessories->Terminal and follow this thread: [http://ubuntuforums.org/showthread.php?t=395819](http://ubuntuforums.org/showthread.php?t=395819) to mount your hard drive.  Then, run the command I gave you earlier.

---

### Post by funkyguy4000 on 2010-02-25
alright so I tried that stuff, it just gives me that error  /dev/sda/mymountpoint in /etc/fstap or /etc/mtab couldn't be found

Or something like that.  So I tried his solution.  And it entaled the sudo command.  I can't use sudo things i guess.  I put in the stuff sudo mount /dev/sda/mymountpoint

and it says

[sudo] password for shannon:

and when i type my password, i'm pressing the buttons down and i'm positive the keyboard works and it's all good but when I type in the password, it's like i'm not typing it.  The little black line thing for typing doesn't move like it usually does when I type.  So i don't know if it isn't accepting it or it's being all secret-like.  Or what.  As of now, I haven't been able to use the sudo command and whenever I try to use the try ubuntu without change to your computer command when booting from the livecd, it just has those squashfs and I/O Buffer issues.

---

### Post by chaanakya_chiraag on 2010-02-26
The terminal doesn't show the password even though it is being typed (It's a security thing :D)

---

### Post by funkyguy4000 on 2010-02-27
okay so thats what I thought it was.
So basically I can't do anything because i'm not in the sudoers file, i'm not an full admin, just a guest.  

Is there maybe anything I could type in the terminal that would be all like fix yourself!

Or something i could do?

---

### Post by chaanakya_chiraag on 2010-02-28
If you could get a livecd up and running for a while (it doesn't necessarily have to be Ubuntu), you could try that command from the livecd, which shouldn't require a sudo password.

---

### Post by funkyguy4000 on 2010-02-28
what to you mean by get it up and running?

I can get to the menu of it but when I try to try ubuntu without any change it does the buffer i/o and squashfs errors.

---

### Post by chaanakya_chiraag on 2010-02-28
If you can boot any livecd until it gets to the desktop/command prompt, post back.  It doesn't have to be an Ubuntu cd; it just has to be Linux :D

---

