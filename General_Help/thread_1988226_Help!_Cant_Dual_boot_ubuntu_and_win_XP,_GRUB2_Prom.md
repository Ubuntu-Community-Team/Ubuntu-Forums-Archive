---
title: "Help! Cant Dual boot ubuntu and win XP, GRUB2 Prompt appears"
date: 2012-05-27
forum: General Help
---

### Post by 4Anket2 on 2012-05-27
Hi! I Used to Dual boot ubuntu and win xp, when yesterday I spent alot on my windows, and when i booted into my ubuntu, a strange prompt with the name "Grub 1.99", and something with ubuntu with it (i think 21ubuntu and another number at the end), i didnt know what to do, so i flipped the whole net to find an answer, what caused something more horrible, i cant boot into windows! I Use My Ubuntu on the USB now, And Im Really frustrated of this situation, please, if its possible, could you give me a solution to this problem, so i could make everything like it was before, and just "lead" me through this process? Ill Be Very Thankful!:)

---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> Hi! I Used to Dual boot ubuntu and win xp, when yesterday I spent alot on my windows, and when i booted into my ubuntu, a strange prompt with the name "Grub 1.99", and something with ubuntu with it (i think 21ubuntu and another number at the end), i didnt know what to do, so i flipped the whole net to find an answer, what caused something more horrible, i cant boot into windows! I Use My Ubuntu on the USB now, And Im Really frustrated of this situation, please, if its possible, could you give me a solution to this problem, so i could make everything like it was before, and just "lead" me through this process? Ill Be Very Thankful!:)

Does your GRUB menu give you the option to boot into Windows? If not, you can try updating GRUB by running the following code in Terminal. It should detect your Windows and your GRUB menu should be updated.

```
sudo update-grub
```

---

### Post by 4Anket2 on 2012-05-27
hi! And Thank you for the first reply, but i didnt had any option to log into windows, and the code you gave me didnt changed nothing (dont worry, i wrote it in the ubuntu terminal), but here is the situation, i boot my PC, it loads, and after the "loading operating system" disappears, the prompt appears. (and BTW, its written "grub 1.99 23ubuntu3")

And Another thing, here what i get when i type:> sudo update-grub
> ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).


---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> hi! And Thank you for the first reply, but i didnt had any option to log into windows, and the code you gave me didnt changed nothing (dont worry, i wrote it in the ubuntu terminal), but here is the situation, i boot my PC, it loads, and after the "loading operating system" disappears, the prompt appears. (and BTW, its written "grub 1.99 23ubuntu3")

I'm sorry, I don't have much more knowledge on this issue, but I think it has to do with GRUB picking up the Windows XP. I don't want to give you false information as I'm not that experienced with GRUB, but you can take a look at this [link.]("https://help.ubuntu.com/community/Grub2/Installing") Also, I believe you can use [Boot-Rapair]("https://help.ubuntu.com/community/Boot-Repair") to reinstall GRUB. I've used it countless times with my Windows XP & Ubuntu dual-boot.

---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> hi! And Thank you for the first reply, but i didnt had any option to log into windows, and the code you gave me didnt changed nothing (dont worry, i wrote it in the ubuntu terminal), but here is the situation, i boot my PC, it loads, and after the "loading operating system" disappears, the prompt appears. (and BTW, its written "grub 1.99 23ubuntu3")

And Another thing, here what i get when i type:

Oh, I experienced that problem today. :lolflag: I used Boot-Repair to fix it. I don't quite understand how it works exactly, but I think it installs GRUB to the MBR of the HDD. 

Are your operating systems on separate hard disk drives or on separate partitions in the same hard disk drive?

---

### Post by 4Anket2 on 2012-05-27
Ok m8, i can access my windows now (i got the OS selection menuat the startup, but Not GRUB's menu), but when i select the ubuntu OS, it shows me the GRUB prompt again, how to fix that???? (yes, i used the boot-repair, this program does magic!, and the two operating systems are on one HDD)

---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> Ok m8, i can access my windows now (i got the OS selection menuat the startup, but Not GRUB's menu), but when i select the ubuntu OS, it shows me the GRUB prompt again, how to fix that???? (yes, i used the boot-repair, this program does magic!, and the two operating systems are on one HDD)

The OS selection menu should be GRUB, the menu that has GRUB 1.99 as the heading with listings such as:


>  [CENTER]GNU GRUB version 1.99-21ubuntu3[/CENTER]

Ubuntu, with Linux 3.2.0-24-generic
Ubuntu, with Linux 3.2.0-24-generic (recovery mode)
Previous Linux versions
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Microsoft Windows XP Home Edition (on /dev/sda1)

The above is how mine looks. 

Okay, you are able to access your Windows now. Great! When you select Ubuntu, does it take you to the OS? 

I assume you used the "Recommended Repair" option from Boot-Repair?

---

### Post by 4Anket2 on 2012-05-27
ok, my list looks like that:

> 
Windows XP Professional
Ubuntu
Windows (default)   <------(this one just appeared) 

And When I select Ubuntu, it takes me to the GRUB Prompt, do you need pics????

And Yes, i used the Recommended Repair!

---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> ok, my list looks like that:



And When I select Ubuntu, it takes me to the GRUB Prompt, do you need pics????

And Yes, i used the Recommended Repair!

Yeah, pics would help. :)

---

### Post by 4Anket2 on 2012-05-27
OK, Here is how my boot menu looks like seconds after i turn on the PC: [IMG]http://ubuntuforums.org/attachment.php?attachmentid=218771&stc=1&d=1338115602[/IMG]

And Here What I Get When I Select "Ubuntu":[IMG]http://ubuntuforums.org/attachment.php?attachmentid=218772&stc=1&d=1338115602[/IMG]

Hope That'll Help!

---

### Post by Shadius on 2012-05-27
Ah! Gotcha! Gimme a second to find the appropriate solution. :popcorn:

---

### Post by Shadius on 2012-05-27
Post the output of the following code:

```
sudo fdisk -l
```

That is a lowercase "L"

---

### Post by 4Anket2 on 2012-05-27
i did't got it, where should i write this?

---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> i did't got it, where should i write this?

Oh, you need to run that in a Terminal. Then highlight what's in the Terminal and copy and paste it here. I forgot to mention since you're unable to boot into Ubuntu, use a LiveCD or a live USB.

---

### Post by 4Anket2 on 2012-05-27
here you go: > ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000eccab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63  1946178359   973089148+   7  HPFS/NTFS/exFAT
/dev/sda2      1946191870  1953523711     3665921    5  Extended
/dev/sda5      1946191872  1953523711     3665920   82  Linux swap / Solaris

Disk /dev/sdb: 4004 MB, 4004511744 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00015686

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7791524     3895731    b  W95 FAT32

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5bb6288e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   312560639   156280288+   7  HPFS/NTFS/exFAT

Disk /dev/sdd: 4004 MB, 4004511744 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x31486d95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63     7821311     3910624+   c  W95 FAT32 (LBA)


---

### Post by Shadius on 2012-05-27
Okay, it appears that your Ubuntu is installed on /dev/sda so we'll need to reinstall GRUB to /dev/sda with the following:

```
sudo grub-install /dev/sda
```

Then update the grub list by running:
```
sudo update-grub
```

---

### Post by 4Anket2 on 2012-05-27
here what i get:
> ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).


---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> here what i get:

We have to mount it, but I am not sure which partition your Ubuntu is on. Was it the 1000.2 GB drive?

---

### Post by 4Anket2 on 2012-05-27
Yep It Was

---

### Post by Shadius on 2012-05-27
Okay, I believe the code to run would be:

```
sudo mount /dev/sda1 /mnt
```

Then try:
```
sudo grub-install /dev/sda
```

---

### Post by 4Anket2 on 2012-05-27
Well, basically now you will see why i warned everybody that i Flipped the net LOL!

cuz here what i get: > ubuntu@ubuntu:~$ sudo mount /dev/sda1 mnt
fuse: failed to access mountpoint mnt: No such file or directory


---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> Well, basically now you will see why i warned everybody that i Flipped the net LOL!

cuz here what i get:

*Slaps self on forehead!* I'm so sorry. It's supposed to be:

```
sudo mount /dev/sda1 /mnt
```

Try it now. Sorry, I'm running on a very small amount of sleep.

---

### Post by 4Anket2 on 2012-05-27
*poop my pants* Here what i get: > ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

---

### Post by drs305 on 2012-05-27
Since you can boot Windows but not Ubuntu, and it's the Windows bootloader you are getting first, you might try looking at the Wubi megathread:
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> *poop my pants* Here what i get:

Run
```
df -Th
```

---

### Post by 4Anket2 on 2012-05-27
@[[COLOR=#DD4814]**drs305**[/COLOR]]("http://ubuntuforums.org/member.php?u=223945") ill take a look at it, thanks!

---

### Post by 4Anket2 on 2012-05-27
> **Shadius said:**
> Run
```
df -Th
```

I did, whats next?

---

### Post by Shadius on 2012-05-27
> **drs305 said:**
> Since you can boot Windows but not Ubuntu, and it's the Windows bootloader you are getting first, you might try looking at the Wubi megathread:
[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

Oh thank goodness you're here! Maybe you can solve his issue. I tried my best, but I'm very inexperienced. :(

---

### Post by Shadius on 2012-05-27
> **4Anket2 said:**
> I did, whats next?

Post the output.

---

### Post by 4Anket2 on 2012-05-27
here: > ubuntu@ubuntu:~$ df -Th
Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs  1.8G   56M  1.7G   4% /
udev           devtmpfs   1.8G  4.0K  1.8G   1% /dev
tmpfs          tmpfs      703M  908K  702M   1% /run
/dev/sdd1      vfat       3.8G  701M  3.1G  19% /cdrom
/dev/loop0     squashfs   673M  673M     0 100% /rofs
tmpfs          tmpfs      1.8G  8.0K  1.8G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      1.8G   80K  1.8G   1% /run/shm
/dev/sdb1      vfat       3.8G  1.5G  2.3G  39% /media/SCHOOL STIK
/dev/sdc1      fuseblk    150G   51G   99G  35% /media/Alex's HD


---

### Post by Shadius on 2012-05-27
You could try this:

[Stuck on GRUB command line]("http://askubuntu.com/questions/32135/stuck-on-grub-command-line")

I have to go now. I hope that link helps you. Sorry I couldn't be of more help to you. When I return, if your problem still isn't fixed, I will try to help again. Good luck. :)

---

### Post by 4Anket2 on 2012-05-27
wait, WHAT?????? WHERE IS MY HARD DRIVE????????

---

### Post by oldfred on 2012-05-27
Do you really have wubi and not a partitioned dual boot. First boot menu looked like a Windows (& wubi) boot menu.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

wubi boots using the Windows boot loader in the MBR and is just a file inside the NTFS windows partition.

From the boot repair post a link to boot info:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or [COLOR=Red]'Create BootInfo' report (Other Options)[/COLOR] & post the link it creates, so we can see your exact configuration.

---

### Post by 4Anket2 on 2012-05-28
Hello, I Just Decided to give up and reinstall ubuntu. but thanks yo everybody who helped! Especially to you @Shadius! You Really helped me!

---

### Post by Shadius on 2012-05-28
> **4Anket2 said:**
> Hello, I Just Decided to give up and reinstall ubuntu. but thanks yo everybody who helped! Especially to you @Shadius! You Really helped me!

Hey 4Anket2, sorry we couldn't solve it for you. :( Is everything working for you now?

---

