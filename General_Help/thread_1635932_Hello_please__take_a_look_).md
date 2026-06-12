---
title: "Hello please  take a look :)"
date: 2010-12-02
forum: General Help
---

### Post by takemylife on 2010-12-02
Hello
As You see i'm a newbie and i'm new to this forum
well i wanted to try the linux operating system
i like it but i wonna make dual boot
so that i will have windows for gaming and linux for other stuff
so i  made 3 partitions (from linux  boot cd) but when i put
windows xp it can't see any partiotion to be installed 
so that it says installation can't  start cause it doesn't find any hard drive installed etc.
so can anybody teach this newbie? :P

---

### Post by lrgmmc on 2010-12-02
windose needs to bee installed first.

---

### Post by takemylife on 2010-12-02
so what can i do now?
I unistalled linux and tryed to install windows but still same error

---

### Post by lrgmmc on 2010-12-02
boot up ubuntu live cd on that pc. then post ```
sudo fdisk -l
```
your going to need to reformate the hard drive to fat32 so that windows can see it.

---

### Post by takemylife on 2010-12-02
well thanks
U mean i have to format from the boot?
I have to boot and delete all partiotions and make new partition fat32?

---

### Post by searchfgold6789 on 2010-12-02
Well, it seems to me that you are in one of three positions. Either you had windows installed, and then made three other partitions on your hard disk on which to install linux and windows; you erased windows and created three partitions on which to install linux; or you had a blank hard disk on which you put three partitions using the live CD: one to install windows on and two to install ubuntu on, or vice versa.

It might help us to know what exactly what your system looks like right now so we can tell you how to install windows and ubuntu so that they play nice with each other.

Please download the [**_boot info script_**]("http://sourceforge.net/projects/bootinfoscript/"), run it from the terminal in the live CD, and paste back the RESULTS.TXT file in Code Tags.

Remember this: you only need an existing windows installation and some free disk space to install ubuntu as a dual boot. The installer will do the rest for you!

Also keep in mind the different file system types. To install windows on a partition it needs to be NTFS. You can select this option when you make the partition. To install linux you need ext4, plus a swap partition.

I'm interested in seeing what you might post back... :D

You don't necessarily have to have windows installed before you install Ubuntu but it makes the setup process easier.

---

### Post by takemylife on 2010-12-02
heh thanks for info im gonna check atm
IM fifghting with this 6 hours now..
I don;t have an idea  of linux i'm now trying to learn it :P

---

### Post by takemylife on 2010-12-02
sorry for double post but... i should copy this to windows live cd?

---

### Post by searchfgold6789 on 2010-12-02
Ummmmm......
What? windows live CD?
What i am suggesting you do is download the script from above, open up a terminal from the Ubuntu Live CD, and then click and drag the boot-script file into the terminal window. It will create a file called results.txt, please attach it into your next post :)

---

### Post by searchfgold6789 on 2010-12-02
Reading that over again, I realized that I should have made it more simple:

[LIST=1]
[*]Boot from the Live CD you made ("Try without installing").
[*]Click [_**here**_]("http://cdnetworks-us-2.dl.sourceforge.net/project/bootinfoscript/bootinfoscript/0.55/boot_info_script055.sh").
[*]Save the file to your desktop.
[*]Open up a terminal (applications>accessories>terminal)
[*]Once it loads type in "sudo " (with the space after it) and do not press enter.
[*]Click and drag that file on your desktop into the terminal windows area.
[*]Press enter in the terminal.
[*]Wait.
[*]Once the results.txt file are on your desktop, post the contents of it back here.
[/LIST]

---

### Post by takemylife on 2010-12-02
naah thanks for the info
Well nothing happens just opens the folder ;P
Im A newbie in linux i told ya ;D
Well  i just loaded partiotions again 
i have 3 2 primary and 1 logic 
the primary's are ext3 and the logic swap

---

### Post by takemylife on 2010-12-02
sudo: /home/ubuntu/Desktop/boot_info_script055.sh: command not found

---

### Post by restorator on 2010-12-02
Windows wont necessarily see the partitions if you if you only have the ext3 partitions. Reformat the first one to NTFS and then you may be able to install windows from your windows install disc.

---

### Post by takemylife on 2010-12-02
i don't have any ntfs choose :/ 
is there any programm i can do it without reboot the pc? 
cause i'm  doing it from linux cd :D

---

### Post by dFlyer on 2010-12-02
Boot your Ubuntu live CD.
From System/Administration reformat your HD With the following partitions if you want to run XP and Dual boot into linux.

1st (Primary) Partition: 32 Bit win or  NTFS
2nd (Primary) Partition: Ext3 or Ext4 depending what version of Ubuntu your using.
3rd. (logical) Partition: Linux Swap.

1. Install Windows XP to the 32 bit partition.
2. Install Ubuntu or what ever version of linux you want to the Ext3/Ext4 partition.

---

### Post by restorator on 2010-12-02
How are you creating the partitions? I assume you are using the live cd and gparted. If not please give details. 

While in gparted right click on the partition and select "format to" and then select ntfs. That should get you back to windows and then we can get to installing ubuntu

---

### Post by takemylife on 2010-12-03
can i have link and details of gparted plz?  :P 
thanks all of you for the help
i really appriciate it

---

### Post by Malta paul on 2010-12-03
You will find gparted in Ubuntu Software center, got to applications>Ubuntu Software center.;)

---

### Post by kanishkdudeja on 2010-12-03
Boot from the ubuntu live cd. Click on try without installing. After it opens up..Click on system -> administration -> GParted Partition Editor.

---

### Post by takemylife on 2010-12-03
thanks for details guys
i should boot from cd?

---

### Post by kanishkdudeja on 2010-12-03
yup.

---

### Post by takemylife on 2010-12-03
i can't make new partition table ntfs why? :|

---

### Post by lrgmmc on 2010-12-03
what is gparted not list ntfs as an option?

---

### Post by takemylife on 2010-12-03
yeah 
i made a new ntfs table
i deleted linux
and windows xp installation still can't see the  hard disk
wtf i'm doing wrong? do i need any programm for dual-boot? :S

---

### Post by takemylife on 2010-12-03
i think i found this error
For a long time i'm searching with my friend (google)
IT seems like windows xp can't recognize SATA hard disk
am i right?

---

### Post by restorator on 2010-12-03
lol yes, I  hadn't thought of that. WinXp before service pack 1 (or was it 2) cannot see sata out of the box. You need to have a disk with sata drivers handy during the install or an XP disk with sp2 or sp3 already integrated. (or an IDE drive...)

---

### Post by takemylife on 2010-12-03
yeah now i have an other prob 
i want format the dvd of prev windows to install the new one
help? :P

---

### Post by lrgmmc on 2010-12-03
so you have a dvd-rw and you want to blank it?

---

### Post by restorator on 2010-12-03
First off if you dont have the sata drivers or you dont have and Xp disc with sp1 2 or 3 your not going to install windows until you get one of those things. But you could still install ubuntu to either a partition or the whole drive, just use the cd and install and you can leave a partiton for windows to be installed later or shrink it later. Its a little trickier to install windows after ubuntu but not hard if you follow instructions properly to reinstall grub.  

But if thats not the case let me see if i get this right.
1)you have an imaged copy of xp with service pack 1 or 2 or 3 on a drive somewhere?
2)you want to burn it to the dvd you already have xp (without sp 1 2 or 3 on)?


is the dvd a rewritable? if so continue, if not you will need a new blank disc. If its a factory disc you will definately need a new disc.
you can then use the ubuntu live cd to fire up your computer or else use another computer and (in ubuntu) use brasero to create a new ISO image from the image file you have, or in windows you can use imgburn or similar. 

(note this all assumes you have a legal copy as we cannot help otherwise).

once you have that it should be simple to reinstall windows, just drop in the disc and startup the computer, follow instructions on the screen, etc.

---

### Post by takemylife on 2010-12-03
I Have a  dvd with installed windows xp  that can't recognize the sata
i dl a version sp3 that recognize them
i go buy a new dvd rom
and go try for 1 last time
if  i dont manage  i don't mind ill need to focus on ubuntu :P

---

### Post by restorator on 2010-12-03
> i dl a version sp3 that recognize them

Did you only download the service pack? That will not work. You need a copy of xp with the service pack already part of the disc. You can however create one if you have 1) a xp disc and 2) a copy of sp3. 3) a running windows computer. You need to use [nlite]("http://www.nliteos.com/index.html"). Follow the instructions on their site (and any questions about it use their forums) to create an xp disc with sp3 installed.

---

### Post by takemylife on 2010-12-04
i downloaded xp with sp3 installed ;D 
thanks all for your help :)

---

