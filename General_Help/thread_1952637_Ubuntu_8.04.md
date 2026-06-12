---
title: "Ubuntu 8.04"
date: 2012-04-04
forum: General Help
---

### Post by Tpadtech on 2012-04-04
Hi-
 
I need some help please. My company and I repair IBM/Lenovo notebooks.  Hard drives have always been an issue as far removing OS pre-loads and formatting.  I had a bunch of kids working for me at one point where one of them loaded a desktop with Ubuntu 8.04 and Gparted.  This all worked great.  Drives got wiped-partitions blown out and corrupt sectors were immediately detected.   This whole process was nothing I ever learned-because I have a ton of work to do everyday.  One by one the kids left and now I do not know to use this machine.  
 
I was able to figure out Gparted.  I can identify the drives and refresh them-but I can not figure out how to wipe the drives. We could wipe up to 12 drives at a time.   I see a "dd" icon on the main desktop-but I can not implement the command to actually wipe the drive.  
 
Would some one please help me?  
 
Tpadtech=clueless on any form of Linux anything
 
thanks!

---

### Post by winh8r on 2012-04-04
In the top left of the desktop there is an "applications" menu select this then select "accessories" then right click on "terminal" and select "add to desktop"

once you open a terminal you can use dd to either zero a drive or write random data to it

The commands are as follows:

to write zeros to a drive
```
dd if=/dev/zero of=[COLOR="Red"]/dev/sda[/COLOR] bs=1M
```
 
and to write random data to the drive use
```
 dd if=/dev/urandom of=[COLOR="Red"]/dev/hda[/COLOR]
```

where [COLOR="Red"]/dev/sda[/COLOR] is substituted for the name of the drive you are wiping

remember it as **of = [COLOR="Blue"]O[/COLOR]utput [COLOR="Blue"]F[/COLOR]ile**

the zeroing option is much quicker than random

hope this helps

---

### Post by Cheesemill on 2012-04-04
Also bear in mind that Ubuntu 8.04 reached end of life 12 months ago and no longer receives any support or updates.

---

### Post by winh8r on 2012-04-04
> **Cheesemill said:**
> Also bear in mind that Ubuntu 8.04 reached end of life 12 months ago and no longer receives any support or updates.

Yes , that too!

I have assumed that the machine is a lab machine and as such is only used for wiping hdd's.

Thanks Cheesemill.

---

### Post by Tpadtech on 2012-04-04
Oh wow-thanks for all of the help. 
 
I will give it a whirl-if a power grid goes out-it wasn't me!
 
I don't use this computer to go online..strictly for formatting.
 
thanks again

---

### Post by winh8r on 2012-04-04
No problem,

just in case you do decide to upgrade it, you can get Ubuntu 10.04.4 LTS from here :

[http://releases.ubuntu.com/lucid/]("http://releases.ubuntu.com/lucid/")

This is a long term support release which will still be supported until April 2013 and is a fairly similar layout to 8.04 in terms of getting around the desktop.

Good luck.

---

### Post by Tpadtech on 2012-04-04
Ok-but just so that I am on the same page.  This part of the code:
 
to write zeros to a drive

Code:
dd if=/dev/zero of=[COLOR=red]/dev/sda[/COLOR] bs=1M
 
If I have multilple drives-then I change the sda-to sdb, sdc..etc...correct? 
 
 and what does the "bs =1M" mean?
 
thanks

---

### Post by Cheesemill on 2012-04-04
bs=1MB means 'use a block size of 1MB'.

By default dd will write one bit of data at a time. By increasing this to 1MB of data at a time you greatly increase the speed of the operatioon.

To check the identifier of the disks attached to the system you can type:
```
sudo fdisk -l
```
into a terminal, this will list all of the drives that are currently attached. Be aware that /dev/sda will probably be the system drive so you want to avoid wiping it, doing so will probably break your system.

---

### Post by Tpadtech on 2012-04-05
Ok-I am still a bit lost.  
 
I need to write random information on the drives, which I know that will take a long time.  Usually was an overnite process.  However, I need write to multiple drives at once.  I have icons of each drive on the desktop-primary drive being "a"-would I just go into the properites of each drive and type the command?
 
thanks

---

### Post by Cheesemill on 2012-04-05
Why are you wanting to write random data? Writing just 0's will be quicker.

You can run the command more than once at the same time, for example:

First find the drives you wish to delete:
```
sudo fdisk -l

[COLOR=DarkRed]Disk /dev/sda[/COLOR]: 64.0 GB, 64023257088 bytes
256 heads, 63 sectors/track, 7753 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x199e199d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   125045423    62522711+  ee  GPT

[COLOR=DarkRed]Disk /dev/sdb[/COLOR]: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x95159515

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953523711   976761824+  83  Linux

[COLOR=DarkRed]Disk /dev/sdc[/COLOR]: 4001 MB, 4001366016 bytes
121 heads, 18 sectors/track, 3588 cylinders, total 7815168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ae951

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048     7815167     3906560    b  W95 FAT32

[COLOR=DarkRed]Disk /dev/sdd[/COLOR]: 4009 MB, 4009754624 bytes
23 heads, 23 sectors/track, 14804 cylinders, total 7831552 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            8064     7831551     3911744    c  W95 FAT32 (LBA)

```From the output you can see that I have 4 drives. Lets say I now want to wipe sdc and sdd:
```
sudo dd bs=1MB if=/dev/zero of=/dev/sdc &
sudo dd bs=1MB if=/dev/zero of=/dev/sdd &

```


If this is too complicated for you there is an easy option.
Download DBAN and burn the downloaded .iso file to a CD, then just boot from the CD and use it to write 0's onto your drives.
No need to use any of the other wipe methods, just overwriting with 0's is enough to guarantee that the data cannot be recovered.
[http://www.dban.org/](http://www.dban.org/)

---

### Post by winh8r on 2012-04-05
If you do decide to use the DBAN method above then you can remove the hard 

drive with Ubuntu on it and put another drive you wish to wipe in its place 

then just run DBAN from the cd drive. It will wipe all the connected hard 

drives simultaneously.

---

### Post by CharlesA on 2012-04-05
+1 to dban, altho I have had issues running it on newer machines with card readers and the like.

The only concern I'd have with running multiple instances of dd at the same time would be both system load and i/o load.

---

### Post by Tpadtech on 2012-04-10
DUE TO THE CUSTOMER WE ARE SELLING TO IT HAS TO BE RANDOM 0 AND 1 AND WHEN WE ENTER THE CODE INTO THE TERMINAL WINDOW AND HIT ENTER ......... NOTHING HAPPENS ... DO WE NEED TO LOGON IN AS ADMIN OR SOMETHING TO RUN CODE INTERMINAL WINDOW ?"
ok-my Boss wanted me to post this.

---

### Post by Cheesemill on 2012-04-10
You wont see any output until the command finishes, this may be several hours for a large drive.

Also there is no benefit to writing random data over writing just zeros, you may want to ask your boss why the customer is insisting upon this method. Writing zeros over the drive is just as secure as writing random data.

---

### Post by Tpadtech on 2012-04-10
well first, thank you to all of you who have replied.  
 
I do have DBAN.  As I mentioned earlier I have Gparted and I also have Acronis.  But what is tied to our Lab computer is Ubuntu and Gparted.  I can hook up around 15 drives at once and delete partitions..yadda yadda..
 
but I just can not get them all to format at once, hence me asking about the code to execute.  
 
the reason for the random data-this is how our customer is asking to have the drives formatted.  we save them a lot of time by sending the drives in this type of format. we understand that this is an overnight process
 
so my boss also wanted me to post this:
 
[LEFT][FONT=Arial][SIZE=2][COLOR=#0000ff]ASK SC[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#0000ff][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=#0000ff]SO AFTER ENTERING [/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#0000ff][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=#0000ff]SUDO [SIZE=3][FONT=Times New Roman][COLOR=#000000]dd if=/dev/urandom of=[/COLOR][COLOR=red]/dev/hda  [/COLOR][/FONT][/SIZE][/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#0000ff][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=#0000ff]INTO WINDOW .. HOW DO WE TELL IF IT WORKING ?[/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#0000ff][/COLOR][/SIZE][/FONT] 
[FONT=Arial][SIZE=2][COLOR=#0000ff]he types in caps for our FRU (lenovo/ibm part numbers) numbers-just easier.  [/COLOR][/SIZE][/FONT]
[FONT=Arial][SIZE=2][COLOR=#0000ff][/COLOR][/SIZE][/FONT] 
 
[FONT=Arial][SIZE=2][COLOR=#0000ff][/COLOR][/SIZE][/FONT] [/LEFT]

---

