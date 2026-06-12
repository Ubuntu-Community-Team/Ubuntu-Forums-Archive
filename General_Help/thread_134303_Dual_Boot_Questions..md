---
title: "Dual Boot Questions."
date: 2006-02-21
forum: General Help
---

### Post by dracule on 2006-02-21
Hi ive searched around and found a video on dual booting but i have a few more questions.

What if i already have windows 98 installed? how do i create a partition?
Is there a step by step guide for dual booting that can be printed?
Does having 2 OS's slow the performance of your machine?

---

### Post by mcwtlg on 2006-02-21
If you already have Win98 you can still install Ubuntu.  You will need to resize your partition first (assuminng you only have 1 hard drive).  After you resize it, you will need to start the Linux install process on the second partition.  Breezy will give you some options and you need to make sure that you install it on the newly created empty space. hda1 will be your Windows partition, you will want to format the other partition to your preferred FS type (I use ext3, but their are others).

Once the install is through, it will want to install grub, which is fine.  It will most likely see your windows partition and offer to let you dual boot, with an entry for  Linux, Linux "safe mode", memtest, and your Windows verison.  If you want Linux to boot if no choices are made, then you are set.  If you are like me and need to have Windows boot (for my lovely Windows using wife) if no choice is made, you will have to modify your boot list config.

Nice thing about Win98 and Ubuntu is that Ubuntu will be able to read and write the Windows (because it is FAT).  Do a bit of research and you will be fine.  I am a noob and I dual booted my WinXP / Ubuntu box first try without any major problems.  I had little things to iron out, but nothing that kept me from booting EITHER OS.

Best of Luck.

---

### Post by dracule on 2006-02-21
thanks. but does having 2 OS's make your comp slower? somepeople say yes while others say no. Some say that windows will take up too much CPU but i dont know how it will do that if its not booted.

---

### Post by akiro.yamamoto on 2006-02-21
Nope ;)
If you boot into Ubuntu, XP will not be running. Therefore it will use 0 CPU cycles.
If you use Ubuntu then install VMware (or some such) then install XP on that, you will be able to run XP in Ubuntu. In that case XP will be using some of your CPU cycles. But that is not what we call Dual Booting, that is running XP in a Virtual Machine (VM) on your Ubuntu Desktop System.
I hope this helps clear it up.

---

### Post by Fred Doolie on 2006-02-21
>If you use Ubuntu then install VMware (or some such)

how do you do that? I get a "Does not work with your kernal" error. So that's kinda the end of that. no?

Please tell a Ubuntu noobee step by step how to get VMWare installed. Either the full one or just the player. Preferably the player since it's free. I can always make the virtual machines on the Winblows side of my system.

---

### Post by SixStringNavigator on 2006-02-21
I'd like to follow up with more questions on dual booting.  I am installing a 160GB drive in my Dell Dimension 8200 and will be installing WinXP Pro and then Ubuntu.  I'll want to use NTFS for Windows.  I understand that you can allocate a FAT32 partition which would allow transferring files between the two OS's.  Can Linux read & write files in the FAT32 partition?

Will Ubuntu have any problems addressing any of the 160GB drive (inside it's own partition) ?

---

### Post by LateNighter on 2006-02-21
I use Windoze Only to Play Games.
 When I'm using Ubuntu, "WHY WOULD I" want to run Windoze IN IT???

 I don't even let my Windoze acess the NET, I shut off my Lan Connection.

 This is JUST me but why would you want to Run Windoze in Ubuntu?:confused: :confused: :confused: 

 If you want to run Widoze setup a Dual Boot.

 That way you don't even have to look at Windoze if you don't want too...
 I Cringe even seeing Windoze on my Boot Selection Screen.

 The only time I ever have to reformat is because Windoze Messes Up...
 I've never had to because Linux has messed up.[-( [-( 

 My wife one time asked me if I could setup Ubuntu to Look and act like Windoze, I said Yea but when I'm running Ubuntu, I don't want to even be reminded of Windoze...  It's bad enough being reminded of it on the Net...

 Just my 2 cents Worth, But to each his Own.

 But if you set up a Dual Boot No Windoze ain't even a Factor and it won't even Slow Up your PC one Bit....:D :mrgreen:

---

### Post by Lux Perpetua on 2006-02-21
[QUOTE=SixStringNavigator]I'd like to follow up with more questions on dual booting.  I am installing a 160GB drive in my Dell Dimension 8200 and will be installing WinXP Pro and then Ubuntu.  I'll want to use NTFS for Windows.  I understand that you can allocate a FAT32 partition which would allow transferring files between the two OS's.  Can Linux read & write files in the FAT32 partition?

Will Ubuntu have any problems addressing any of the 160GB drive (inside it's own partition) ?[/QUOTE]
Yes, Linux can read and write to FAT32. Actually, Windows can even read and write to ext2/3 with the proper driver, since it is an open specification, but I have no experience with that (never really needed to). NTFS is a pain, though (read-only support, no write support, for Linux).

---

### Post by alan.mckinnon on 2006-02-22
[QUOTE=Fred Doolie]>If you use Ubuntu then install VMware (or some such)

how do you do that? I get a "Does not work with your kernal" error. So that's kinda the end of that. no?

Please tell a Ubuntu noobee step by step how to get VMWare installed. Either the full one or just the player. Preferably the player since it's free. I can always make the virtual machines on the Winblows side of my system.[/QUOTE]

VMware needs a whole bunch of drivers that are not in the standard kernel, so it has to make them itself after vmware itself has been installed. VMware can't supply the driver files ready made as they can differ quite a lot from one kernel version to another.

All you do is start a terminal and run this command:
sudo vmware-config.pl
The program will make it's own drivers and store them in the right place for your current kernel. From then on it's a simple matter of running vmware and creating new virtual machines as always.

When you next upgrade your kernel you will have to do the procedure again (but only once for each upgrade). The Best solution would have been for the drivers to be in the standard kernel. But they are not, so this one extra step is needed.

BTW, Windows doesn't have this problem as Microsoft have the absurd idea that any driver must be able to run on any kernel they ever made, ever. This might seem like a good idea but it really isn't (it means that Microsoft can never really fix their mistakes properly)

---

### Post by dracule on 2006-02-22
Is there a way to automatically boot into linux on start up, then once in linux, select boot up windows, which would then just run windows? I dont think my computer is fast enough to run both linux and windows at the same time, but i dont want to select ubuntu everytime i start up my computer because i will only run windows for games. so in a simplified sentence:
Is there a way that once in ubuntu, you can reboot into windows, without having to select windows on the start up screen, but once in windows, you woundnt run linux?

---

### Post by dracule on 2006-02-22
Id appreciate it if you answered my previous question too, but is there a chance that dual booting will lead to the deletion of windows on installation of ubuntu? and how big is that chance?

---

### Post by Ramses de Norre on 2006-02-22
?? stopping linux and starting windows = rebooting
and yes you have to pick it from the grub menu then. You can choose which one is started if you haven't made a choice for a number of seconds which you can choose too.
I'd say just install that dual boot, it's pretty simple. and if you don't like it you can always kick ubuntu and make an extra windows partition of it.
Or when you really like it kick windows;)
You learn a lot on trying it.

---

### Post by Ramses de Norre on 2006-02-22
The change that windows is deleted is really small, but I don't say it's impossible.. Being eaten by a crocodile tomorow isn't impossible either..
The best is to repartition before installing (do a couple of defragmentations before you resize your partitions). Or even better: just get a new harddrive for ubuntu. 
Then just make the right choice in the partition section of the installer, your first hd (IDE controller 1, master) is hda and the first partition of it is hda1 the second hda2,... 
the slave of your first IDE controller is hdb, master of second hdc and so on. Sata disks are sda - sdd followed by the partition number.
You can ask whether you're right, because choosing the wrong one could delete your data.

---

### Post by dracule on 2006-02-22
OK thanks, i might get a hd(frys has a 500 gb for about $90 but i only use 20gb now so i might just get a partition) now here is what i think that i have to do, but i want to verify before i get started.

1. Defrag my hard drive.
2. set up 30% partition for Windows, 69% for ubuntu, and 1% for the swap program.
3 set the linux partition to be the active one.
4 edit my bios so that it will boot from cd.
5 place ubuntu in the cd drive and restart my computer.
6 Install ubuntu under default
7 let ubuntu install grub 
8 set the grub partition to be active.

---

### Post by steveneddy on 2006-02-22
I agree, a second HD is the best option. During install put about 1 Gig for the swap and the rest for Linux. 

Update to as much RAM as you can afford, preferably around 512 mb. 

UPDATE WINDOWS! Make sure that the Windows side is updated and stable. And don't forget to back up your data on Windows. 

Install the HD and boot Windows to make sure the HD is OK and that you did the job right. THEN, put the Ubuntu install CD in the drive and restart.

The first HD will be hda and the second will be hdb. Install on hdb. use EXT3 file system. 

Good luck.

---

### Post by Fred Doolie on 2006-02-23
[QUOTE=alan.mckinnon]VMware needs a whole bunch of drivers that are not in the standard kernel,[/QUOTE]

Well, I got it working, thank you, but Winblows under VMWare is worse than Windoze running natively. I'll just dual-boot. :rolleyes:

---

