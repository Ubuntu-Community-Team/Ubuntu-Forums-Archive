---
title: "Ubuntu 11.04 partition number 83 Value is out of range."
date: 2011-06-29
forum: General Help
---

### Post by bolkonski on 2011-06-29
Hi Guys,
my partition should be linux but I can't allocate it using * because the partition number (1-7): 83
Value is out of range. I want to allocate everything to one big linux partition with just a small partition for windows for warranty purposes.I don't need all those other partitions which I got probably from trying out different Ubuntu versions. I didn't know they were there! I'd really appreciate any help.
Best wishes
bolonski

steve :~$ sudo fdisk /dev/sda
[sudo] password for steve: 

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2bab359d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       75213   604143616    7  HPFS/NTFS
/dev/sda2           75213       77826    20986849+   f  W95 Ext'd (LBA)
/dev/sda5           75213       76190     7846948    7  HPFS/NTFS
/dev/sda6           76190       77312     9011200   83  Linux
/dev/sda7           77312       77826     4126720   82  Linux swap / Solaris

Command (m for help): a
Partition number (1-7): 83
Value out of range.
Partition number (1-7):

---

### Post by FormatSeize on 2011-06-29
The prompt is asking you for a partition number. That's the one through seven. You are getting this error because 83 is not between 1 and 7. Input the partition number (sda[number]) that you want to put the Linux partition on. You won't get a response. Then push "t" (for ***t***ype). Then tell it which type, which is where you put the 83.
 
I would recommend using:
```
cfdisk
``` instead of fdisk. It's a tad easier to manage things properly.

---

### Post by bolkonski on 2011-06-29
Hi FormatSeize and thanks for replying.
This is what I got. The cfdisk only gave me fatal error so I used fdisk. Any ideas?
bolonski

Partition number (1-7): t
Partition number (1-7): sda6
Partition number (1-7): 6
Hex code (type L to list codes): L

 0  Empty           24  NEC DOS         81  Minix / old Lin bf  Solaris        
 1  FAT12           39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 2  XENIX root      3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 3  XENIX usr       40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 4  FAT16 <32M      41  PPC PReP Boot   85  Linux extended  c7  Syrinx         
 5  Extended        42  SFS             86  NTFS volume set da  Non-FS data    
 6  FAT16           4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 7  HPFS/NTFS       4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility   
 8  AIX             4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt         
 9  AIX bootable    50  OnTrack DM      93  Amoeba          e1  DOS access     
 a  OS/2 Boot Manag 51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O        
 b  W95 FAT32       52  CP/M            9f  BSD/OS          e4  SpeedStor      
 c  W95 FAT32 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs        
 e  W95 FAT16 (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  GPT            
 f  W95 Ext'd (LBA) 55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
10  OPUS            56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
11  Hidden FAT12    5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor      
12  Compaq diagnost 61  SpeedStor       a9  NetBSD          f4  SpeedStor      
14  Hidden FAT16 <3 63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary  
16  Hidden FAT16    64  Novell Netware  af  HFS / HFS+      fb  VMware VMFS    
17  Hidden HPFS/NTF 65  Novell Netware  b7  BSDI fs         fc  VMware VMKCORE 
18  AST SmartSleep  70  DiskSecure Mult b8  BSDI swap       fd  Linux raid auto
1b  Hidden W95 FAT3 75  PC/IX           bb  Boot Wizard hid fe  LANstep        
1c  Hidden W95 FAT3 80  Old Minix       be  Solaris boot    ff  BBT            
1e  Hidden W95 FAT1
Hex code (type L to list codes):

---

### Post by bolkonski on 2011-06-30
Hi Guys
Judging by the lack of feedback, I'm beginning to think that my problem falls into 2 possible categories: too simple or too complicated. I have a detailed tutorial about how to allocate(using gparted) an existing windows partition to ubuntu 11.04 by Techotopia. However, some users had problems. Can you recommend it or another suitable one based on the specifications i have posted? I am really grateful for your past help and am impressed by the dedication of this community. I cannot imagine any windows tech guy seeing to me as one of your colleagues did.
Best regards
 bolonski

---

### Post by blueridgedog on 2011-06-30
I am trying to understand your issue:

```
Command (m for help): a
Partition number (1-7): 83
Value out of range.
Partition number (1-7):
```

83 as a partition number is indeed out of range.  In the above spinet the system is asking for the partition you want to edit and "83" was entered rather than a partition number (from one to seven).  Can you explain in more detail what you are trying to do?

If you want to change the type, at the above screen, his "p" to print the partitions, pick the number you want to edit (1 to 7), then enter it when you are asked for the partition number.

---

### Post by Ginzell on 2011-06-30
Hi Bolkonski,
I happen to know nothing about this but following what was being posted, since I'm looking into taking some space from my Windows harddrive side -I'm wondering about this:
You did this below
*********
Partition number (1-7): t
Partition number (1-7): sda6
Partition number (1-7): 6
Hex code (type L to list codes): L
*********
You did get to what was supposed to be done but here's what I'm wondering
Partition number (1-7) : 6 <--you would enter that -then there would be no response from the system according to FormatSeize - so my question is did you type "t" then enter 83 or did that Hex code entry just pop up? 
Just a thought.

---

### Post by bolkonski on 2011-06-30
Hi Ginzell 
Thanks for answering. While going over what you said. wrote sudo fdisk etc in the terminal and jimpef the gun by writing sda6. I should have written "a" I think.Here's what I got :

Command (m for help): sda6
Building a new sun disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.
Then I wrote "a" and got the following:
Command (m for help): a
Partition number (1-8): sda6
Partition number (1-8): 6
Warning: partition 6 has empty type
Dumbstruck!! All I want to do is eliminate all the partitions and have an Ubuntu OS from which I can access my full harddisk 600 gb. I wanted to keep a bit of windows in case I need tech support which the warranty still covers.Grateful for any advice.
bolkonski

---

### Post by Ginzell on 2011-06-30
I'm sorry, I'm still confused as to what you did.  
It should be 
Partition number (1-7): 6 (then it will do nothing and you type "t" then 83)
Is it just not showing up that you're typing the "t" and "83" ? 

At any rate, I'm going to be doing exactly what you are as soon as I do some saving of my files and make a Windows recovery disc.  I want most of the Windows side for my Ubuntu too.  But I will be using the gparted program to do it, I'm not sure what you're doing.  I see you're using the fdisk but I don't know why because you don't want to get rid of it all from what I'm understanding from you.  I always thought fdisk only deletes partitions and makes new ones.  Well, of course that's my understanding of fdisk on the Windows side, I don't know what it does when used in Ubuntu.

---

### Post by dandnsmith on 2011-06-30
bolkonski:
If you favour using fdisk, I recommend either a read of the man pages (man fdisk), or use fdisk /dev/sda, and then print the help (by using m) as suggested by the program.
Then you can either delete the partitions one by one, or create a new partition table (be careful which type you select). Having a clean partition table, you'll be able to create the partitions as you wish (remembering to keep some space for swap, and some for your special partition).

Messages on-screen are there to help you!

---

### Post by bolkonski on 2011-06-30
hi there,
I eliminated my windows partition using gparted and following a tutorial.
I get to sudo gedit / etc/fstab having arrived there successfully and am told to "add the following line to mount the new partition" I do so and put it at the end. Then I get the warning below. and am told line 12 is bad. Maybe you can see what's wrong. I've tried separating the "0"s by 1 2 and no spaces. No luck.
Please help
Best regards
bolkonski



 (gedit:2458): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory 
 steve@steve-MS-7366:~$ sudo mount /voll 
 _[mntent]: line 12 in /etc/fstab is bad _
 mount: can't find /voll in /etc/fstab or /etc/mtab 
 steve@:~$ df -h /voll 
 Filesystem            Size  Used Avail Use% Mounted on 
 /dev/sda6             8.5G  5.6G  2.6G  69% / 




	  # /etc/fstab: static file system information. 
 # 
 # Use 'blkid -o value -s UUID' to print the universally unique identifier 
 # for a device; this may be used with UUID= as a more robust way to name 
 # devices that works even if disks are added and removed. See fstab(5). 
 # 
 # <file system> <mount point>   <type>  <options>       <dump>  <pass> 
 proc            /proc           proc    nodev,noexec,nosuid 0       0 
 # / was on /dev/sda6 during installation 
 UUID=4cd051b9-f88d-4a3f-ac82-9756e83cedb8 /               ext4    errors=remount-ro 0       1 
 # swap was on /dev/sda7 during installation 
 UUID=972b1944-1493-4ce1-a781-959473b5f8dc none            swap    sw              0       0/dev/sda1 /voll ext4 defaults 0 0

---

### Post by Ginzell on 2011-07-01
Sorry I took so long to get back, got wrapped up doggy business.  :D

I really don't know what that error means, I am new to Ubuntu several weeks and I am still learning.
However, I see you said you eliminated your Windows - are you saying you deleted it all together?  I thought you wanted to keep a little piece of it, you change your mind?  
I am hoping to get around to doing mine tomorrow, (or today rather since it's 3am) it took me hours just to make the set of recovery discs for Vista.  Maybe when I actually get into it, I can see what's going on.
One question - did you use gparted from a live CD?  (I'm sure you came across that in your tutorial but just in case you didn't...)

---

### Post by bolkonski on 2011-07-01
hi there,
Don't leave me hanging here guys.
I eliminated my windows partition using gparted.
I get to sudo gedit / etc/fstab having arrived there successfully and am  told to "add the following line to mount the new partition" I do so and  put it at the end. Then I get the warning below(Please see previous post). and am told line 12 is  bad. Maybe you can see what's wrong. 
Please help
Best regards
bolkonski

---

### Post by bolkonski on 2011-07-01
Hi Ginzell
Sorry I just saw your post. I am new to Ubuntu like you.
  I eliminated my Windows keeping a little piece  of it.
I used gparted from a live CD. The tutorial was good and everything went better than expected. I'm sure there's just some space or tiny code missing from my gedit file.I hope someone helps me out here. I can't mount mu main 600+ old windows partition until this is solved. I have so little space on this ubuntu partition.Best of luck with your Ubuntuuing.
bolkonski

---

### Post by Wim Sturkenboom on 2011-07-01
```

# swap was on /dev/sda7 during installation
UUID=972b1944-1493-4ce1-a781-959473b5f8dc none swap sw 0 0/dev/sda1 /voll ext4 defaults 0 0
``` is wrong;you're missing a newline

```

UUID=ef260aa3-f22f-4730-8517-8546c15cba30 none            swap    sw              0       0
/dev/sda1 /voll ext4 defaults 0 0

```
Don't copy the first line with the UUID as that came from my system. You must also have a directory called /voll so it can be mounted.

To get back to the original question; in bold what you are supposed to do.

```

wim@aa0:~$ sudo fdisk /dev/sda

WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003255d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         918     7367680   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2             918         981      509953    5  Extended
Partition 2 does not end on cylinder boundary.
/dev/sda5             918         981      509952   82  Linux swap / Solaris

[B]Command (m for help): t
Partition number (1-5): 1
Hex code (type L to list codes): 83
[/B]
Command (m for help): 

```

You also need to format the disk using mkfs.

At the end, gparted or so might be easier as it can do it all for you


PS
please place commands and output between [noparse]```
 and 
```[/noparse] tags

---

### Post by bolkonski on 2011-07-01
Hi Wim and thanks for taking an interest.
I did exactly as you said and got the results below. You're right, /voll does exist.
bolonski
steve@:~$ sudo gedit /etc/fstab
[sudo] password for steve: 

(gedit:3361): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.AM5GXV': No such file or directory

(gedit:3361): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:3361): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NY4TXV': No such file or directory

(gedit:3361): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

---

### Post by bolkonski on 2011-07-01
Wim,
When I re-write:: "sudo mkdir /voll" i get the message below:
mkdir: cannot create directory `/voll': File exists

So it does exist, but something in the last line is wrong. But what? I copied your (Wim's) last line and in the same place. I had done previously to no avail. By the way I got as far as : "sudo gedit /etc/fstab" using a gparted's live cd.
Thanks 
bolkonski

---

### Post by Wim Sturkenboom on 2011-07-01
I don't think you have to worry about the gtk error; it seems related to the list of recently used files and as such should not affect the actual modifying of fstab. As long as /etc/fstab is modified.

Can you (re)post the content of your current /etc/fstab?

Who is the owner of /voll ?

//Edit:
And what is the error that you get ?

---

