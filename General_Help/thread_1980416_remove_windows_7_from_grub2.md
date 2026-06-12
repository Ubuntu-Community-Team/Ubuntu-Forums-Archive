---
title: "remove windows 7 from grub2"
date: 2012-05-15
forum: General Help
---

### Post by satish_j on 2012-05-15
I had Lucid,Windows XP and Windows 7 on my system.
After experiencing problem with Win7,i formatted its partition to ext4 and installed 12.04 on it.But this did not remove the Windows 7 entry from grub menu.
When I start the computer, it goes to GRUB, and has the option for Precise,Lucid and Windows 7, not XP. When I choose windows 7 I goes to its own boot loader and the has windows xp(shown as 'Earlier version of windows'). So basically I have to go to 3 boot loaders for windows xp to start. What I would like to do is have XP on grub and remove Win7 from grub and,as I click on one it starts booting that OS instead of taking me to another boot loader.
Any Ideas how to achieve it:)

---

### Post by zombifier25 on 2012-05-15
Run this in the terminal:
```
sudo update-grub
```

---

### Post by satish_j on 2012-05-15
> **zombifier25 said:**
> Run this in the terminal:
```
sudo update-grub
```

tried it already with no success..

---

### Post by zombifier25 on 2012-05-15
Looks like Windows 7's BOOTMGR is not removed. You must reinstall XP's NTLDR if you want that annoying process to go away.
Sorry, I don't know the exact process of doing so. You should wait for someone else.

---

### Post by Mark Phelps on 2012-05-15
When you installed Win7, after you had XP, it wrote its boot loader files to the XP partition.  Thus, when you removed Win7, it's boot loader files remained.

What MIGHT work is the following:
1) Remove the BOOTMGR folder and files from your XP partition
2) Reboot - into Ubuntu
3) Do "sudo update-grub" again.  This time, without the Win7 boot loader files, it should find the XP loader (NTLDR) and add that to GRUB instead.
4) Reboot and see if that worked.

Sorry, but that exhausts my XP boot knowledge (since I haven't used it in years).

---

### Post by satish_j on 2012-05-16
> **Mark Phelps said:**
> 
1) Remove the BOOTMGR folder and files from your XP partition

Where can i find the BOOTMGR folder on XP partition.Also,would it affect XP if i delete it?

---

### Post by wilee-nilee on 2012-05-16
> **satish_j said:**
> Where can i find the BOOTMGR folder on XP partition.Also,would it affect XP if i delete it?

If you get no definitive answer that you feel comfortable with I would go here they are quite helpful.

[http://www.sevenforums.com/](http://www.sevenforums.com/)

This one is a bit if a conundrum, I have not seen this sort of a problem for a long time on this forum, maybe not at all really.

If you get it fixed be sure to tell us how, it would be nice to know.

---

### Post by ivikas on 2012-05-16
**Make a backup of the file you are going to edit**

Important:See if you can boot to your Windows XP.If you can boot to Windows XP.Skip this paragraph-->if you cannot,then you have to use the windows xp repair disk to write
windows xp loader to the MBR(Master Boot Record.)When you do this grub will be removed from the MBR and ubuntu will be inaccessible.So you need to reinstall the grub from the ubuntu live cd.This process is bit lengthy and tricky but guides are available on google search.  

Login as root in your lucid and open this file.

```

/boot/grub/grub.cfg

```

Locate the below line which says windows,either remove this entry or comment it out using a '#' sign before each string.
 
```

menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set=root 42688EFF688EF0C9
	chainloader +1
}

```

---

### Post by satish_j on 2012-05-16
@ivikas,how would i then access XP if Win7 bootloader is commented in grub.cfg.
I have to first make sure that XP is listed directly in Grub list alongside Win7 and other Linux distros and that it is bootable.
Also,command 'sudo update-grub' will update the grub.cfg file again, since Lucid is using Grub2.
I had earlier thought of removing Grub complately ad then using Live Cd to install grub,but i neeeded to avoid booting from CD since my system is a bit old and needs one HD to be disconnected in order to connect DVD-Drive.
I was thinking there may be away to achieve what i want without needing to boot from CD..

---

### Post by wilee-nilee on 2012-05-16
> **satish_j said:**
> @ivikas,how would i then access XP if Win7 bootloader is commented in grub.cfg.
I have to first make sure that XP is listed directly in Grub list alongside Win7 and other Linux distros and that it is bootable.
Also,command 'sudo update-grub' will update the grub.cfg file again, since Lucid is using Grub2.
I had earlier thought of removing Grub complately ad then using Live Cd to install grub,but i neeeded to avoid booting from CD since my system is a bit old and needs one HD to be disconnected in order to connect DVD-Drive.
I was thinking there may be away to achieve what i want without needing to boot from CD..

To be honest that post is incorrect I think, it looks wrong anyway, your W7 and XP boot are entangled, puting the XP boot back in the mbr just does not sound right to get past this.

They also do not tell you how to get grub back.

---

### Post by satish_j on 2012-05-22
Finally,I had to connect the dvd-drive and install mbr again.
Then,from a Live CD,installed Grub again on mbr which detected XP.
I have now Winxp directly in my grub boot menu along with other Linux distros..problem solved..
closing the thread..

---

