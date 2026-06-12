---
title: "Dual boot on HP Pavillion dv6-6060ep"
date: 2012-08-10
forum: General Help
---

### Post by oteixeira on 2012-08-10
[FONT=Calibri][SIZE=3]Hello to all.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I bought a  HP Pavillion dv6-6060ep (i7 processor) running Microsoft Windows Home Premium but i would like to put the machine in dual boot with Ubuntu 12.04 (64 bits).[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I already tried once but the Ubuntu installation failed and the machine stopped working and I had to restore the entire system as it came from factory.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The machines come with 4 partitions on the hard disk so I had to delete one of them for my attempt to install Ubuntu.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]I used a document I found by googling and it seemed to be detailed and explicit. I already review it and was unable to find what I did wrong.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]This is why I’m asking if someone can point me a good document to follow in order to achieve my goal.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3]Thanks in advance for any kind help.[/SIZE][/FONT]
Octavio

---

### Post by Mark Phelps on 2012-08-10
Since you already have four partitions, that is the maximum allowed. Simply removing HP_TOOLS is not the solution -- as it is too small to be of any use.

So first, copy all the files and folders inside the HP_TOOLS partition into your Win7 OS partition.  

Second, open up the Win 7 Disk Management tool.  NOW, you can remove the HP_TOOLS partition.

Third, shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

Fourth, you will need a way, in the future, to restore Win7 to its present state -- and you can do that without using the Recovery partition.  Download and install the free version of Macrium Reflect.  Hook up an external drive, and use MR to image off the Win7 OS and its boot partition to that drive.  Then, use the MR option to create and burn a Linux Boot CD.

Now, using that CD, you have the ability to restore your current Win7 setup from that backup. 

Fifth, you can now go back into the Win7 Disk Management tool and remove the Recovery partition. Do not format the free space, leave it as is.

Finally, BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by forhpm on 2013-02-10
Hi, I must be a total git but I'm trying to copy your instructions in this thread to the letter. How do I copy the HP_Tools files and folders into the Win7 OS directory? I can't even find it in Computer, which shows me Local Disk (C: ) and Recovery (D: ). In C:, there is a folder called HP_TOOLS_mountHPSF but it is empty. There is also a folder called HP which has four subfolders: Bin, Data, HPQware and support. In D: there are a few subfolders,: $Recycle.bin, _MSSETUP.T, System Volume Information and then other icons that say boot, hp, preload, Recovery and system.sav. When I click on these, the right hand of the window shows message from HP: "Recovery Partition, Warning. This areo of your hard drive [or partition] contains files used to perform a system recovery. Do not delete or alter any of these files. Any change to this partition could prevent a system recovery in the future."

Thanks.

---

