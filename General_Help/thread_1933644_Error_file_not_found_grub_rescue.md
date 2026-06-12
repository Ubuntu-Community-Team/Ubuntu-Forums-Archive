---
title: "Error: file not found grub rescue"
date: 2012-02-29
forum: General Help
---

### Post by sirriffsalot on 2012-02-29
Greetings!

I'm awesome...really... when it comes to screwing things up. I had a dual boot going in the past on my computer, and when I wanted to freshly install Ubuntu Studio instead of the "vanilla" Ubuntu taking up the "linxu" partition bit, I managed to delete the Ubuntu partition, which is fine, but in the process I also sloppily removed the swap within the partitioning page as well, now making my computer unable to see any direction signs and thus ending me up with a grub rescue prompt...

The windows part is still intact, and I have tried suggestions such as 

"Boot from the Windows XP/Vista/7 installation CD, and select the Repair (R) option. Select the correct partition, and then enter the Administrator account password. At the command prompt run the following commands:

fixmbr (C:\WINDOWS\fixmbr.exe)

fixboot (C:\WINDOWS\fixboot.exe)

Type 'exit', and the computer will reboot."

but those commands don't exist, apparently, and I have gone through the possibilities that the install/repair CD has to offer my "tabbing" through ALL of the options...A normal bootrepair doesn't help since the windows vista install CD can find nothing wrong...

So bottom line, if the worst case scenario is that I will have to reinstall vista too, that is fine, as long as I can get some access to my windows partition to save some crucial files... If things are going to have to get much worse, please shoot me! However these two solutions are unwelcome unless it is really necessary... So, I am begging for dear life that someone will come up with something that saves the day... My life depends on not being shot!!

By the way, the reason things got messed up were because the Ubuntu Studio install would never go all the way and deliver... It would always fail at some point after the partitioning stage, so I had to abort and here I am. But frankly I did not have a 100% control, obviously, and yes not taking a backup was a naive and stupid thing. Still, a hero is always welcome! 

Thank you:)

---

### Post by sirriffsalot on 2012-02-29
Any other suggestions?

---

### Post by chipbuster on 2012-02-29
Simple solution if you have any sort of removable media would be to boot a LiveCD and use that to transfer all of your critical files off of the drive, then install off of it. 

If you don't have removable media, things get trickier :(

---

### Post by sirriffsalot on 2012-02-29
Yea, I could pull that off, but what then? Re-install Vista completely, then add Ubuntu Studio on top? Blank sheets? Or...?

Gonna find a laptop and produce the magical LiveCD with Ubuntu on it and see if I can save my precious files. In the mean time, how does this look like to you? Can't hurt?

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to the "restore vista" part, obviously, and thanks for your help so far:)

---

### Post by imachavel on 2012-02-29
Lol fix mbr fix boot are windows command line options when you boot to the recovery console portion of the windows cd. Are you dual booting windows and Ubuntu? You can try booting to gparted cd and setting the boot flag to windows(it doesn't like to share)

Simpler option, you want to fix any file system shared boot sector and grub menu?? Boot to the live cd and open terminal Ctrl+alt+t, and try to sudo apt-get install boot repair. Try selecting boot repair. This almost always works, also you can also create a boot script and upload it at the forum. But the issue is it might be reading the grub that is on the Linux live cd and not the hdd. If ou can get to another computer, download boot repair disk .iso, burn it to a cd then boot to it, then select repair boot. Tell me what you think and any questions you have, lspci, no wrong command. Actually I don't remember, if you can boot the live cd and load the GUI, get to the desk top, open a terminal, there should be a command to show your partition table, but I forgot what it is. Once again this will most likely show the partition table of the cached boot sector of the live cd you are booted to, wherever and however that is cached, not what is on the hdd

---

### Post by imachavel on 2012-02-29
> **chipbuster said:**
> Simple solution if you have any sort of removable media would be to boot a LiveCD and use that to transfer all of your critical files off of the drive, then install off of it. 

If you don't have removable media, things get trickier :(

I know you can view separate partitions on the hdd in Linux OS when booted to a partition on the HDD and pull out files. Will it work the same way with a live cd? OP might need to emote hdd and transfer files with a USB to hdd interface(Sata or IDE), then reinstall. I'm assuming OP gets dev/sda grub issue and actually can boot to HDD. I suppose chkdsk or fsck wouldn't be a bad idea, but I don't know how to use chkdsk from bios, if you can get any grub options(I know the file system won't load), try using fsck, can't be too safe.

Idk what grub issue are you getting OP, did you say one partition will load but not the other? Or did you say neither partition will load?

---

### Post by sirriffsalot on 2012-02-29
The thread I linked fixed the dual-boot problem in such a way that I could access my windows partition again, thank the lord who is all lol. If that hadn't worked though, your suggestion would have been the next one on the list of attempts. Now, I'll simply save all the files and go crazy in trying to partition it correctly, and if all goes to hell then I do a fresh reinstall of Vista and then add Ubuntu Studios. I get in, out, no one gets hurt - hopefully!

Thanks for taking time out to write all that though, I am sure others will find both my results and links and your suggestions helpful! Cheers mate:)

--> Leo

---

### Post by sirriffsalot on 2012-02-29
Cheers mate, I worked things out to such an extent that things will work out however bad this partition setup get. Worst scenario is I reinstall everything, which is more than a timely thing to do considering what this computer has been through:) Thanks for your help though, people looking at this post later will probably be saved time by your suggestion! Cheerz!

--> Leo

---

