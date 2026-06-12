---
title: "Error: no such partition. grub rescue&gt;"
date: 2011-08-25
forum: General Help
---

### Post by Jigsaw501 on 2011-08-25
Hello! I am the epitome of ignorant when it comes to this sort of thing so bear with me here..
A friend of mine is pretty computer savvy and installed ubuntu on my computer months ago just to as something to learn.. I didn't care and never used it because all of my music/data is on my windows partition and I don't know how to transfer it.. Ever since he installed it I've had a grub menu open startup to choose two versions of ubuntu, windows 7, and some sort of recovery mode/memory test option.. I always ignore and choose windows no problems, until now.. My computer has started to become slower then i'de like so I decided to reinstall the os. However I have a pretty new windows 7 i3 laptop that didnt come up with a disk. I'm supposed to be able to key "0" upon startup and access a hidden partition that will restore my computer to it's "out-of-box state".. I tried this with noo luck at all.. I looked for support from windows as to why the reinstall/reset wouldn't work only to learn it seems ubuntu is somehow blocking my ability to access the hidden partition.. For awhile I ignored because I dont know how to uninstall ubuntu and was to lazy to learn. But I got fed up with my slow computer so I tried fallowing a guide on YouTube (probably not smart) on how to uninstall ubuntu.. I installed/ran Easybcd and then deleted some partitions, as told to in the guide.. I immediately restarted y computer to check if keying 0 would now work and to see if ubuntu was gone and....

My computer is a vegetable. I can't access either os.. Allthat happens is the option to go to setup utility or boot manager.. And then shortly after this appears:

error: no such partition.
grub rescue>

This is terrible for me as I desperately need access to my computer. What do I do?? I've spent hours on these forums and found people with the same issue however all the suggested solutions haven't worked for me.. I have nearly everything backed up so I just need to know how to completely reset my computer.. 

Please help! Quickly! :O

Cheers ^_^

---

### Post by oldfred on 2011-08-26
Do you have a windows repairCD? Or the Ubuntu liveCD used to install Ubuntu or any other repair cd/tools?

You just need to install windows boot loader to the MBR. You can use your windows repair tool. Or you can install a windows boot loader that works like windows in the MBR. 

Not sure but many windows repair CD's or EasyBCD may also have ways to fix by reinstalling the boot loader.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:

[COLOR=Red]BootRec.exe /fixMBR [/COLOR]  #updates MBR master boot record  do not run if you still want grub

From Ubuntu liveCD or many other Linux repair CDs.
Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

---

### Post by christopher.wortman on 2011-08-26
> **oldfred said:**
> Do you have a windows repairCD? Or the Ubuntu liveCD used to install Ubuntu or any other repair cd/tools?

You just need to install windows boot loader to the MBR. You can use your windows repair tool. Or you can install a windows boot loader that works like windows in the MBR. 

Not sure but many windows repair CD's or EasyBCD may also have ways to fix by reinstalling the boot loader.

How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:

[COLOR=Red]BootRec.exe /fixMBR [/COLOR]  #updates MBR master boot record  do not run if you still want grub

From Ubuntu liveCD or many other Linux repair CDs.
Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

He just stated that he did not have a Windows CD. Depending on the system, you can call the manufacturer like Dell and they will send you the disk for a nominal fee. I think I have seen them run about $30 USD. Then you have the disk forever and should it ever mess up again you have it to reinstall. It is obviously Windows 7 as he stated, so the "/vista" thing is really pointless. Quit using geek talk on people. Just pop the disk in and it will tell you how, just read the instructions and everything will be ok :)

---

### Post by mbuller10 on 2012-01-02
From Ubuntu liveCD or many other Linux repair CDs.
Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

that worked for me, to hell with ubuntu for never recognizing my graphics card

---

