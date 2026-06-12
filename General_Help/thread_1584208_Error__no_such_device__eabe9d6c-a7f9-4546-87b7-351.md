---
title: "Error : no such device : eabe9d6c-a7f9-4546-87b7-3511e3888a545 after  updating Ubuntu"
date: 2010-09-28
forum: General Help
---

### Post by aGia2009 on 2010-09-28
Hi, i am a newbie at linux and although i am a hard working person, i love to spend my time learning about new staff. 
   I always try to find out how to work things out on my own , and i only resort asking for help only on grave situations.
 

I spend a lot of hours trying to learn linux
(i actually use Ubuntu  10.04, and i installed them to try and learn c++ with eclipse ). 
   Today i did some upgrading with upgrade manager and after promting me  to restart i now get this message :
  Verifying DMI Pool Data .....
error : no such device : eabe9d6c-a7f9-4546-87b7-3511e3888a545

ps1: i had ubuntu istalled with WUBI , which means i also had win 7 on them
ps2: when typing ls , i only get (hd0) (hd1)   (i got two harddrives)   but i dont get (hdX,i) i=0 to whatever.
ps3: please help me because i need my pc running again, i got important files in there.
    i presume i have a partitioning problem (when i type 
ls (hd0,1)/boot i get a responce   : unknown filesystem
ps4: l get to see only grub rescue and it appears that set prefix and root, all work.


 i would like you to guide me into restoring this

                           Kind regards, Tilemahos  (thanks to quackers for suggesting i should start a thread about this)

Thanks i  made a new thread. The situation i am dealing with is pittyfull.   I even restored my bios to defaults which at first gave me a new message after  dmi pool data .    There was update success and then it wouldnt move. After a restart now i am back to where i was.

---

### Post by Quackers on 2010-09-28
aGia2009, welcome to the Ubuntu Forum.
It would be better if you start your own thread - possibly with the heading
error : no such device : eabe9d6c-a7f9-4546-87b7-3511e3888a545

---

### Post by bcbc on 2010-09-28
Quick fix with WUBI is to install the windows bootloader. Most likely you installed grub2 to the drive MBR when you installed a grub-pc update.

So for Win7 boot into repair mode and run "bootrec.exe /fixmbr" - this will reinstall the windows bootloader.

You can also use lilo - it can be made to do the same thing as the windows bootloader and you can install it from a live CD if you don't have a windows disk handy (ignore warnings regarding booting linux):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

---

### Post by psusi on 2010-09-28
So you all got an automatic update today that caused this?  Which version of Ubuntu are you running?  If it is the beta of Maverick, then there was an update to grub2 today... if it is causing problems that certainly needs looked into, though you should be posting in the maverick forum.

---

### Post by drs305 on 2010-09-28
aGia2009,

Welcome to the Ubuntu forums.  :-)

I've merged and combined your posts from the previous thread with this one. 

I will monitor the thread and if I can add anything to what the other posters have said to help you solve this problem I will. If you aren't seeing the Windows menu when the system first boots, *bcbc* has most likely given you the solution.

---

### Post by aGia2009 on 2010-09-28
Thank you so much for your support. Its really warming to find people like you.
    Anyway , my distro is Ubuntu 10.04.  I have indeed checked 2 small boxes one for each hard drive . While updating i was asked to make a selection i didnt obviously understand.

QUOTATION: Most likely you installed grub2 to the drive MBR when you installed a grub-pc update.
Thats what i probably did.
  I could probably burn a dvd with windows 7 or use a live cd.  But i dont have a live cd and neither do i know how to create one. Is it better to use a win 7 dvd or a live cd? 
Btw my pc is an old amd 64 x2 4400+.

---

### Post by bcbc on 2010-09-28
> **aGia2009 said:**
> Thank you so much for your support. Its really warming to find people like you.
    Anyway , my distro is Ubuntu 10.04.  I have indeed checked 2 small boxes one for each hard drive . While updating i was asked to make a selection i didnt obviously understand.

QUOTATION: Most likely you installed grub2 to the drive MBR when you installed a grub-pc update.
Thats what i probably did.
  I could probably burn a dvd with windows 7 or use a live cd.  But i dont have a live cd and neither do i know how to create one. Is it better to use a win 7 dvd or a live cd? 
Btw my pc is an old amd 64 x2 4400+.
I don't think it makes any difference whether you install the windows bootloader or lilo - this type of bootloader just looks for the partition with the boot flag and transfers control to it. It's not like grub which is a lot more 'complex' (as evidenced by it's growing pains).

So whichever is more convenient for you - that's what I would suggest. 

you can download a windows repair CD image pretty quickly from the net - it's smaller than an ubuntu .iso so might be easier ([http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/))

On the other hand, if you are going to play with Ubuntu some more it's useful to have a live CD.

---

### Post by aGia2009 on 2010-09-29
Finally , its time for me to say this post must be closed.
In a few words i used a win7 disk , unchecked windows 7, selected command line and typed bootrec /fixboot and then bootrec /fixmbr.   You saved me :)
   After a few hours everything felt like nothing happened.
ps: i kept in mind i must obtain a live cd. I ll try to download one just in case.

---

### Post by Quackers on 2010-09-29
aGia2009, if you are satisfied that your questions are answered it may help others if you mark the thread as "solved". Near the top of the forum page if you click on Thread Tools and select solved.

---

