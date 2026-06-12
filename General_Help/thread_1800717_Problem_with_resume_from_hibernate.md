---
title: "Problem with resume from hibernate"
date: 2011-07-09
forum: General Help
---

### Post by kubco2 on 2011-07-09
Hello,

I have problem with resuming after hibernate, it is about 50% chance  that computer restart when i want resume, then it starts boot normally  and all my work is lost. 

acer aspire 3820tg
ubuntu 11.04
builtin hibernate on partition

If you need logs. I can copy here if you write how I get it.

Thanks

I try uswsusp s2disk ... on resume it always stops in half of process


I used mainly hibernate, but I'm lost now :(. 

Can someone help, please .

---

### Post by ElToro on 2011-07-09
I have had similar problems with *hibernate* on several laptops and I have simply stopped using it on those that cause trouble; I alter the power saving settings to just change to *blank screen* when idle, and alter hibernation to *never*...

---

### Post by techunit on 2011-07-09
How much swap do you have? You can find this information in Disk manager. you should have about 1GB more than the amount of ram you have installed in your computer. If  you don't you will run into problems. If yo need to extend the swap partition restart into your  Ubuntu install medium, and use gparted.

---

### Post by kubco2 on 2011-07-09
I have about 3GB swap .... and use 32bit ... But I use only 1-2GB of RAM max. but if I know when the problem is small swap partition. Then Hibernate stops on copying to swap.

Edit: 
RAM: 2.8GB(553MB used)
SWAP: 2.9GB(0% used)

---

### Post by kubco2 on 2011-07-10
bump

---

### Post by kubco2 on 2011-07-11
Today I reinstalled and completly change partitions and their place on disk. Swap part has 5GB now.

On fresh installation it still restart on resume.

Edit: I tried memtest86(in grub menu and live cd) and after initialize(blue background and tables) notebook restarts.

---

### Post by Marky FAQ on 2011-07-11
motherboarrd Suspen option:S1 or S3

---

### Post by Marky FAQ on 2011-07-11
motherboarrd Suspend option:S1 or S3

---

### Post by tortugo23 on 2011-07-11
> **kubco2 said:**
> Hello,

I have problem with resuming after hibernate, it is about 50% chance  that computer restart when i want resume, then it starts boot normally  and all my work is lost. 

I used mainly hibernate, but I'm lost now :(. 

Can someone help, please .

I have the same problem. Hibernate seems to force quit, loose data and shut down programs improperly. :confused:

---

### Post by kubco2 on 2011-07-11
Marky FAQ:  what do you mean? ... In windows is no problem with hibernate

---

### Post by kubco2 on 2011-07-11
> **ElToro said:**
> I have had similar problems with *hibernate* on several laptops and I have simply stopped using it on those that cause trouble; I alter the power saving settings to just change to *blank screen* when idle, and alter hibernation to *never*...

It is not solution because when I am on critical battery, I need hibernate ... no suspend no shut down.

---

### Post by tortugo23 on 2011-07-11
> **kubco2 said:**
> Marky FAQ:  what do you mean? ... In windows is no problem with hibernate

Same situation again!

[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]In Windows I set my laptop to hibernate when I close the lid. When I shut the lid it hibernates.

In Ubuntu I set my laptop to hibernate when I close the lid. When I shut the lid it force quits, improperly closing programs, and losing data.[/FONT][/FONT][/COLOR]

---

### Post by Savio2010 on 2011-07-12
This is a common problem i have seen, I had faced this problem in Ubuntu 10.10 also.
Things when more complicated for me when I upgraded to Ubuntu 11.04. My swap partition got encrypted automatically. My swap was active at boot time but resuming from hibernation always failed.

I have written a blog post on how to solve this problem Go to my [blog]("http://bit.ly/eA8oGX").

Hope that helps you.

---

### Post by tortugo23 on 2011-07-12
> **Savio2010 said:**
> This is a common problem i have seen, I had faced this problem in Ubuntu 10.10 also.

I have written a blog post on how to solve this problem Go to my [blog]("http://bit.ly/eA8oGX").

Hope that helps you.

Thank you! I got to step two where I received the response: 

swapon failed: Device or resource busy

---

### Post by kubco2 on 2011-07-13
Savio2010: thanks for respond.

I tried your solutions but I have still problems.

---

### Post by Savio2010 on 2011-07-13
Post the outputs of the following here

[I]sudo fdisk -l | grep swap

[/I]*blkid | grep swap*
*cat /proc/swaps*
*cat /etc/initramfs-tools/conf.d/resume*

---

### Post by kubco2 on 2011-07-14
```

*sudo fdisk -l | grep swap*
/dev/sda7           77117       77823     5668945   82  Linux swap / Solaris

sudo *blkid | grep swap*
/dev/sda7: UUID="82d053e6-4b8f-40f5-a8c0-2dc77d863302" TYPE="swap" 
[I]
cat /proc/swaps[/I]
/dev/sda7                               partition    5668940    29408    -1

*cat /etc/initramfs-tools/conf.d/resume* 	
RESUME=UUID=82d053e6-4b8f-40f5-a8c0-2dc77d863302

```

I think all is OK, because sometimes it resume. As I wrote: it is 50% chance to fail resume

---

### Post by Savio2010 on 2011-07-14
> **tortugo23 said:**
> 
[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]In Ubuntu I set my laptop to hibernate when I close the lid. When I shut the lid it force quits, improperly closing programs, and losing data.[/FONT][/FONT][/COLOR]

I find all your configuration correct. Recheck your configuration w[COLOR=#000000][FONT=Times New Roman][FONT=Verdana]hen you shut the lid[/FONT][/FONT][/COLOR]. if everything is fine then
check if your swap is active
```
cat /proc/swaps
```and then
Regenerate your initrd. 
```
sudo update-initramfs -u

```Reboot.

Good Luck:popcorn:

---

### Post by kubco2 on 2011-07-15
help pls

---

### Post by kubco2 on 2011-07-20
bump

---

### Post by gpgdx on 2011-08-04
I have exactly the same problem. Resuming from hibernate fails randomly (about 50% of the times I suppose). And I also have acer 3820TG machine and Ubuntu 11.04. I checked the suggestions pointed in this thread already, but situation is still the same.
Thanks in advance for help, 
- Gopal

---

### Post by alextacy on 2011-08-11
Same problem here; computer will not resume from hibernate or suspend, and this happens 100% of the time.  The notebook (Asus U41sv) will also not power down when I put into either hibernate or suspend modes... motors keep running & the machine stays hot, which indicates that it isn't hibernating properly.

Had to install Win7 on my new machine for work & had this problem since then; running Ubuntu 11.04 on my old (old, old) Dell I had no problems with either function.

I'm not a techy so not very clever at this stuff.   The initial install was Win7 prof... then I tried to install Ub11.04 from a disc as per usual but couldn't, so then did the install from the ubuntu website (all automatic but only giving me a max 30GB partition for Ubunu).

This is going to sound dumb, but how do I check my swap capacity? (sorry, i'm an idiot!)

I have looked in 'System Monitor / resources' and it says i have 5.8GB ram, but only 256MB of swap available...  previous threads suggest that avail swap should then be up around 6 or 7 GB?? (did i read this correctly?)

How do i go about changing this, if it is possible at all?

*sudo fdisk -l *

gives me the following: 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       25497   204697600    7  HPFS/NTFS
/dev/sda3           25497       60802   283584512    7  HPFS/NTFS

I take it that this means no swap is available

[I]sudo fdisk -l | grep swap

[/I]gives me nothing

*sudo swapon /dev/sdaX*

results in:

swapon: /dev/sdaX: stat failed: No such file or directory



Any ideas?  Sorry i'm out of my depth!

Cheers, 

A

---

