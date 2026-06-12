---
title: "how to access bios partition? and repair"
date: 2011-12-25
forum: General Help
---

### Post by dang_boy on 2011-12-25
my windows xp 

corrupted bios partition and memory erase fail

how repair bios partition? and how access bios partition..

---

### Post by dino99 on 2011-12-25
there is no partition for bios, its a rom.
remove the power cord, remove the bios battery, wait a few minutes, insert the battery back and set the power cord. Then try to boot again. Is your bios updated ?

note: you need to set again your custom preferences into the bios

---

### Post by dang_boy on 2011-12-25
I know

remove the bios battery and then 8 -9 hour wait, ( No change)
 bios update and then no change 

erase hard drive and perfect hard drive (all sectors "0000" perfect disk) and freeze continue

---

### Post by dino99 on 2011-12-25
so when/where did you get the freeze ? Set the bios using default. Test the memory banks, one by one. You need to locate the problem. Is your hardware tatooed ? ( HP, Dell often does; meaning that the user is not allowed to tweak partitions if the mostly hidden factory partition(s) is /are shrinked/moved/...) Solution in such case is the low level format that only seagate tool can do.

---

### Post by dang_boy on 2011-12-25
No 
 real problem bios partition and bios partitions block

blocked partitions have and invisible

(Linux-based Livecd) Parted magic cd have 

how see block partitions?

---

### Post by kurja on 2011-12-25
> **dang_boy said:**
> No 
 real problem bios partition and bios partitions block

blocked partitions have and invisible

(Linux-based Livecd) Parted magic cd have 

how see block partitions?

I don't know what you mean by "bios partition", as bios does not have a disk partition.

Do you get an error message saying something about "bios partition"? If that's the case then only thing I can think of is that there's a problem with the memory where bios resides, and if that's the case then you're looking at replacing the motherboard.

---

### Post by dang_boy on 2011-12-25
Bios partition have 

Quote:
Some times it&#8217;s necessary to work with  UFS (the default filesystem on FreeBSD, OpenBSD, NetBSD, etc.) from your  linux box. Here I&#8217;ll explain how to do so by configuring your kernel in  order to enable UFS read/write support. We&#8217;ll focus on FreeBSD.
 Also, as you should know, FreeBSD uses  its own hard disk partition scheme on your PC. It requires only one  entry in the primary partition table of your disk and manages it  similarly to DOS extended partitions, putting in its first sector a new  partition table in BSD disklabel format. So we&#8217;ll enable support for  reading these disklabels; otherwise we just will be able to mount the  root &#8216;slice&#8217; of FreeBSD but not the partitions &#8216;inside&#8217;.
  
**0. Preparing your kernel**

  You may already have support for UFS and  BSD disklabel format, but I&#8217;ll assume that you have built your kernel  by your self and/or don&#8217;t have those options enabled.
 So, let&#8217;s get into the menu configuration of your kernel (I&#8217;m using Linux kernel 2.6.32):
 
 cd /usr/src/linux
make menuconfig
 Now, we are going to activate these options:
 -> File systems
-> Miscellaneous filesystems
    <*> UFS file system support (read only)
      
[*] UFS file system write support
 It&#8217;ll look like this:
 [CENTER][IMG]http://casidiablo.net/wordpress/wp-content/uploads/2009/12/linux-kernel-menuconfig-ufs.png[/IMG] [/CENTER]
 **Important:** write support for UFS2 is on development and could be dangerous. Use it at your own risk [IMG]http://casidiablo.net/wordpress/wp-includes/images/smilies/icon_wink.gif[/IMG] 
 Now, we&#8217;ll enable the FreeBSD disklabel support:
 -> File systems
    -> Partition Types
        
[*] Advanced partition selection
          
[*] PC BIOS (MSDOS partition tables) support
          
[*]    BSD disklabel (FreeBSD partition tables)
 It&#8217;ll look like this:
 [CENTER][IMG]http://casidiablo.net/wordpress/wp-content/uploads/2009/12/linux-kernel-menuconfig-ufs-2.png[/IMG] [/CENTER]
 OK&#8230; with these options enabled we just need to compile our kernel and install it:
 make && cp arch/x86_64/boot/bzImage /boot/kernel-2.6.32
 **Note:** I&#8217;m assuming you already know how to work with the kernel&#8230; the line  above will work fine for me, but some of you guys will use other kind  of settings for your boot loader (for instance, those of you who use  initramfs). In conclusion: I expect you know how to compile and  configure your kernel for this kind of situations.
  
**1. Looking for partitions names**

  When working with FreeBSD, the disks  device names are like this: /dev/ad0s3a. But, as we are working with  Linux, we&#8217;ll have the traditional /dev/sda* or /dev/hda* names. So,  thanks to the FreeBSD Disklabel support that we&#8217;ve just added, we can do this in order to know the devices names:
 cat /proc/partitions
 You&#8217;ll get something like this:
 major minor  #blocks  name
8        0  244198584 sda
8        1   41624383 sda1
8        2  158497290 sda2
8        3   39076695 sda3
8        4    5000184 sda4
8        5     524288 sda5
8        6    4194304 sda6
8        7    5223424 sda7
8        8     524288 sda8
8        9   28610391 sda9
Quote:

bios/pc partition have

---

### Post by kurja on 2011-12-25
Okay I don't know about working with kernels and in either case I can't really help you with your problem, but none the less your BIOS does **NOT **have it's own disk partition as it resides on it's own dedicated memory chip on your computer's motherboard.

I'm guessing you mean the *boot *partition?

---

### Post by dang_boy on 2011-12-25
yes
 boot partitions block and invisible

I bios,pc,boot,dos,  names confused
bios partition and pc partition and dos partition and boot partition, the same thing

how see block boot partitions ?

---

### Post by coffeecat on 2011-12-25
@dang_boy, in your first post you refer to Windows XP and then in post #7 you seem to have copied and pasted an unattributed quote from somewhere else that would appear to be about BSD, although it does refer to the Linux kernel. Whether that is relevant to your problem is not clear.

What operating systems do you have installed on that computer? What happens when you try to boot up? Why do you think you have a boot partition and why do you think it is damaged?

---

### Post by dang_boy on 2011-12-25
Windows xp and parted magic livecd have 

how find block partitons ?  PLEASE 

  go crazy >>> Please help 

real problem block partitions and block boot sectors

---

### Post by West201 on 2011-12-25
Does your bios have a system recovery option ?

---

### Post by dang_boy on 2011-12-25
No 
Intel processor and phonix bios...  

(Linux based) parted magic livecd and terminal window have 

blocks for 1-2 command  and parted magic aaaaaa enter

---

### Post by MG&amp;TL on 2011-12-25
I'm not sure anybody is understanding you.

Please post in a calm and detailed way, researching and answering the questions asked of you. Then we can help you!

Boot a linux live cd and take a screenshot of the gparted window. Then post it here.

---

### Post by dang_boy on 2011-12-25
boot linux cd
gparted   just hard drive have and no block partitions 

please blocks for help 

Intel/pc partitions blocked 

Block partitions dev/sdd.../dev/sda..../dev/sdb..../dev/sdc and  
How delete dev/sdd.../dev/sda..../dev/sdb..../dev/sdc partitions

---

### Post by MG&amp;TL on 2011-12-25
A screenshot?

Also open a terminal and **post the output** of

```
sudo fdisk -l
```

---

### Post by dang_boy on 2011-12-25
This is partitions dev/sdd.../dev/sda..../dev/sdb..../dev/sdc  hidden and how screenshot?  

I'm for code need...  bios partitions for code and device partitions for code and unallocate repair code

---

### Post by MG&amp;TL on 2011-12-25
[http://www.jonathanmoeller.com/screed/?p=3448]("http://www.jonathanmoeller.com/screed/?p=3448")

BIOS does not have partition, as far as I know, you cannot write to it without the aid of manufacturer's programs.

Please run the terminal command I posted.

---

### Post by MG&amp;TL on 2011-12-25
[QUOTE=dang_boy][http://www.google.co.uk/search?q=%22bios%20partition%22&hl=en&num=30&lr=&ft=i&cr=&safe=off&um=1&ie=UTF-8&tbm=isch&source=og&sa=N&tab=wi&ei=73P3Ttz9NujT4QTto_SfAg&biw=1366&bih=551&sei=9XP3To-AE-n44QT-ncmNCA](http://www.google.co.uk/search?q=%22bios%20partition%22&hl=en&num=30&lr=&ft=i&cr=&safe=off&um=1&ie=UTF-8&tbm=isch&source=og&sa=N&tab=wi&ei=73P3Ttz9NujT4QTto_SfAg&biw=1366&bih=551&sei=9XP3To-AE-n44QT-ncmNCA)[/QUOTE]

The BIOS does not have a partition; if it did, it would be scarily easy to make it not boot.

What your google search shows is the MBR, an area of the disk BIOS hands over to to tranfer control to the bootloader, which then boots your OS. 

Please keep support threads in support threads. :)

Oh, and please could you provide data for us to help you with, so far we have no clue what is going on. :confused:

---

### Post by Mark Phelps on 2011-12-26
The fdisk command will list the partitions on your drive.  And, the parameter is a lowercase L, not a one.

Once we see the output of the fdisk command, we will be better able to advise you.

However, you need to tell us WHAT the problem is -- not what you want to do about it.  As others have said, BIOS does not have a partition, so that can't be repaired.

---

### Post by nema.arpit on 2011-12-28
First question : 

What your mother tongue / language ? 
Post in mother language as well if possible.

Next:

Boot linux CD
Start **GParted** 
Take photo
Post here

Start **terminal**  :[INDENT]Alt+F2   ;  
type [B]gnome-terminal   ; 
[/B]Press enter
[/INDENT]type :  

[INDENT] sudo fdisk -l
Press enter
[/INDENT]  Take photo
Post here

---

### Post by dang_boy on 2011-12-28
> **nema.arpit said:**
> First question : 

What your mother tongue / language ? 
Post in mother language as well if possible.

Next:

Boot linux CD
Start **GParted** 
Take photo
Post here

Start **terminal**  :[INDENT]Alt+F2   ;  
type [B]gnome-terminal   ; 
[/B]Press enter
[/INDENT]type :  
[INDENT] sudo fdisk -l
Press enter
[/INDENT]Take photo
Post here
my problem aaaaaa Freeze hard drive,   But wipe try, defrag try, 1-2-3 sectors edit and last sectors edit then wipe try

memory views, FFFFFF bad algorithms  
bios views, FFFFFF bad algorithms   

hard drive views, 00000000000 all algorithms perfect and continue freezee 


L&#304;STEN TO ME

memory views, FFFFFF bad algorithms           "advanced hex editor" program have  
 bios views, FFFFFF bad algorithms            ""bios rom explore"" program have

---

### Post by MG&amp;TL on 2011-12-29
:shock:

I'm sorry, but I doubt anyone understood that.

Perhaps as the poster above suggested, you could post in your mother tongue and english, then maybe we could help a bit more.

Or, alternatively, you could look at one of the region-specific sub-forums.

---

