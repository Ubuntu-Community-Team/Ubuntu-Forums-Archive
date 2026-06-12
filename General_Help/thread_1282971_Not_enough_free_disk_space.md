---
title: "Not enough free disk space"
date: 2009-10-05
forum: General Help
---

### Post by GGreen on 2009-10-05
I am having problems with my disk space. I can't complete updates. The error message says "The update needs a total of 226M of free disk space on '/'. Please free an additional 199M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'." I tried this but didn't work.

I am also unable to download new messages with Thunderbird. The error message says "There is not enough disk space to download new messages. Try deleting old mail, emptying the trash folder, and compacting your mail folders, and then try again." I tried this and didn't work.

Also I have noticed Thunderbird is duplicating messages and saying there is new mail. I will have no new messages and then I will have 1200 new messages. I don't know if that is related.

I have Ubuntu and Vista installed. I had an issue installing Ubuntu initially and reinstalled. Now it shows 2 instances of Ubuntu. I have used Gparted to change partition size but am unsure if I did it correctly. I had this problem once before and installed Logical Volume Management and that helped then but now I am stuck.
I would like to delete the unusable Ubuntu and allocate as much partition space to Ubuntu without deleting Vista. I do not like Vista but there are some things that won't work with Ubuntu.

Any help would be greatly appreciated

---

### Post by mikewhatever on 2009-10-05
Can you post the output of **df -h** from Applications->Accessories->Terminal.
Looking at the picture you posted, there is only one linux partition, sda5, and it is nearly empty.

---

### Post by XCan on 2009-10-05
That's peculiar, what is the output of ```
 df -h 
```

Edit: Mike beat me. :p

---

### Post by Intrepid Ibex on 2009-10-05
It seems that your NTFS partition is mounted as /boot and /host, but you got no partition mounted as /, which is kinda weird. Was that picture taken with live cd?

Anyways you could post the content of /etc/fstab =).

Also you got way too big swap partition (twice your RAM is usually enough) and there's almost 20gb of empty space between /dev/sda2 and /dev/sda3.

Yeah and ext4 is newer and better than ext3 =), cheers.

---

### Post by tsger on 2009-10-05
if you copy the contents of /etc/fstab and post them, that will be helpful.

---

### Post by louieb on 2009-10-05
looks like your booting to a WUBI (inside widows) install of Ubuntu. also looks like you have a partition set aside for Ubuntu on the hard drive - its got plenty of disk space. 

Just to be sure before giving a suggestion - Please download the [Boot Info Script - SourceForge.net]("http://sourceforge.net/projects/bootinfoscript/")  

Running it wiil create a file RESULTS.TXT  Put it in your next post - please use code tags - its long. 
To run 
```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by GGreen on 2009-10-05
Thank you all for the quick responses.  The original screenshot was from gParted.  I am attaching results of df -h.  I tried using the terminal for /etc/fstab and sudo bash ~/Desktop/boot_info_script*.sh but didn't get any usable results.  I've attached it also.

Any instructions on how to clean up my disk partitions would be appreciated.  I've tried researching on this and other sites and did what you saw on the screenshot with gParted.  I need to make use of the unallocated space and delete the partition(s) for the Ubuntu install that I messed up on the 1st install.

---

### Post by GGreen on 2009-10-05
If anyone knows how to resolve the issue with the e-mail duplicating in Thunderbird, I would appreciate the reply.  I deleted some mail and emptied trash and deleted some downloads.  I had zero new messages, then it started downloading 3559 new messages.  They were messages that I deleted and also duplicates of messages that were already downloaded that it had already duplicated 4 or 5 times.

---

### Post by louieb on 2009-10-05
Not much help with email but 1st are you connected to an IMAP or POP server. If POP is the option set to delete messages on the server after download? 

Check out - [How to recover lost disk space]("http://ubuntuforums.org/showthread.php?t=1122670")
and [Check your trash]("http://ubuntuforums.org/showthread.php?t=898573")

Just a short term fix. Really should get a regular Ubuntu install working. You already have the dangerous part done (you have a partition ready to install).

About the boot info script. Did you download it?
Have you changed the default download location in Firefox edit>preferences?   If so need to change the **~/Desktop **part of the command to wherever you are downloading to.

---

### Post by GGreen on 2009-10-07
LouieB,

Thanks for straightening me out on boot info script.  I've attached with this message.  Tell me what do I do to get a regular Ubuntu install?  I thought I did already.  My computer will boot to Ubuntu or Vista.  BREAK IT DOWN BARNEY STYLE!!!  Slow motion will work also!

---

### Post by louieb on 2009-10-07
Had a look a the results.txt file. Looks like your running Vista on a Acer PC.  Your current Ubuntu install is inside Vista (a WUBI install).       

Before you start.  I want you to download [EasyBCD]("http://neosmart.net/dl.php?id=1") in Vista. (you will use later to set up the Vista boot loader to dual boot Ubuntu. 

Also having a [Super Grub Disk ]("http://linux.softpedia.com/progDownload/Super-Grub-Disk-Download-8071.html") handy is a good thing too. I would not setup a dual boot without having one around. 

This is your partition table. /dev/sda5 is where you tried to install Ubuntu the 1st time.  But for some reason the install quit or you told it to stop. 


```

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8f46763

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    24,563,384    24,563,322  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048   215,539,703   190,961,656   7 HPFS/NTFS
/dev/sda3         256,499,712   262,791,559     6,291,848   7 HPFS/NTFS
/dev/sda4         262,807,335   488,392,064   225,584,730   5 Extended
[COLOR=Red]/dev/sda5         262,807,398   467,909,189   205,101,792  83 Linux
/dev/sda6         467,909,253   488,392,064    20,482,812  82 Linux swap[/COLOR] / Solaris


```I would try installing again  (I'm a little rusty using live CD I normally use the text base installer so I'm going of memory)

[LIST]
[*] Boot the Ubuntu install CD (do not open it in Windows you boot to it)
[/LIST]

[LIST]
[*]Select Install.
[*]Until you get to partitioning stage just select the defaults
[*]Choose manual partitioning
[*]Select  /dev/sda5 - click on edit - 3 things to set
[LIST]
[*]use as - choose ext3
[*]format - yes check the box
[*]mount point - / (root)
[/LIST]
 
[*]click continue - should tell you its going to format /dev/sda5 and /dev/sda6 - thats what you want -click ok.
[*]When you get to the installation summary screen you will see a button labeled **Advanced - click it**.
[*]This is where you will tell the installer** not **to put GRUB in MBR  
I want GRUB put in the boot sector of the Linux install. tell to install grub in ```
/dev/sda5
```
[*]Click OK - click continue - let the installer finish.
[/LIST]
After the installer has finished reboot Into Vista. Install and run easyBCD. Let it configure your Vista boot loader to let you choose the new Ubuntu install.

---

### Post by GGreen on 2009-10-17
Thanks for your help LouieB.  

I uninstalled Ubuntu and reinstalled with your instructions.  I set up the partions with 30 gigs to root, 10 gigs to swap, and 90 gigs to home.  I didn't know to do this when I first set up Ubutu.  

Your advice on burning a Super Grub Disk was helpful.  It was difficult to get Ubuntu uninstalled properly.  When I went to boot to Ubuntu, it wouldn't.  The Super Grub Disk worked great.  One issue though.  A couple of times when I turned my computer on, it gave me options to boot to Windows XP and Windows 2000 **_ONLY_**.  This strikes me as odd because this computer only has Vista and Ubuntu installed.  It has never had anything else.  I had to use the Super Grub Disk again to get it to give me the right selection of operating systems.

Again...thanks LouieB and all others who posted here.

---

