---
title: "Unable to boot from Ubuntu after installing Windows 7"
date: 2011-10-28
forum: General Help
---

### Post by mumdluri on 2011-10-28
Hi,

I have installed Ubuntu OS from Windows XP using Wubi installer on D-Drive. Due to some reason recently I have uninstalled Windows XP and installed Windows 7 on C-Drive.

Now I can boot only to Windows 7, I am unable to use Ubuntu. Is there way to work with Ubuntu as usual?

Regards,
Bala

---

### Post by veggis on 2011-10-28
check out this link
 [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by lordievader on 2011-10-28
Did you install wubi on the XP drive/partition? In other words did you install the files on the XP drive? How did you remove XP? By formating the drive/partition?

Because if the answer to both questions is yes, then you are in deep trouble. What wubi does is create a file on the Windows drive and enables a boot from that file. If this file is deleted your complete Wubi installation is wiped. Or in other words, all the files you had on the wubi install are then gone.

Hope this is a clear explanation, if not feel free to ask.

---

### Post by shashi20008 on 2011-10-28
yeah are are a few ways to do this. If you want everything as it was before you need to use a third party program called EasyBCD. Google it, download and install. Run EasyBCD and follow following steps:
1. Select add/remove entries from left panel.
2. In "Add an entry" subsection select Linux tab and then select "Wubi" in drop-down menu following 'type' field. 
3. In name field select whatever name you want to appear in the bootloader.
4. Click "add entry" button, click "save", and exit.
5. Now open a command prompt, by selecting "run as administrator" from shortcut menu.
6. Run command

**bcdedit**

7. Copy the identifier value you see in the "Real-mode Boot Sector" section. It will look like {*device_id*}
8. Run following command to set your D drive (as you say) as root partition for ubuntu entry.

**bcdedit /set {*device_id*} partition=D:**

note: Replace 'D:' by proper drive letter if you have ubuntu installed in different drive.

9. Run this command to set path for ubuntu bootable files inside the partition.

**bcedit /set {*device_id*} path \ubuntu\winboot\wubildr.mbr**

note: If you have changed the default location of wubi files you will need to write the actual address of folder relative to partition. Although you probably wont need to do that. simply copy-paste and execute the commands.

---

### Post by mumdluri on 2011-10-28
Thanks for your kind reply.

Actually My XP OS is affected with Virus, so I formatted the C-drive/partition and then installed Windows 7. 
Ubuntu was installed on different drive/partition using Windows Wubi installer.

---

### Post by mumdluri on 2011-10-28
Hi [shashi20008]("http://ubuntuforums.org/member.php?u=1357995"),

I have used EasyBCD and followed the steps you mentioned. When I restart my machine I got Ubuntu Linux bootable option to choose, but choosing this given me the following:

Try (hd0,0): NTFS5: No wubilder
Try (hd0,1): Extended:
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (hd0,4): NTFS5: No wubilder
Try (hd0,5): Extended:
Try (hd0,5): NTFS5: No wubilder
Try (hd0,6): Extended:
Try (hd0,6): NTFS5: No wubilder
Try (hd1,0): FAT32: No wubilder
Try (hd1,1): invalid or null
Try (hd1,2): invalid or null
Try (hd1,3): invalid or null
Try (fd0): invalid or null
Error: Cannot find GRLDR in all devices.

I really don't under what does it mean.

---

### Post by mumdluri on 2011-10-28
HI,

The problem has been SOLVED. What I did is, just copied all the **files from**** \ubuntu\winboot\ **to USB flash drive and rebooted the system with USB drive as my primary bootable drive. Then choosen Ubuntu linux from OS list to load.

You know, I am typing this post from Ubuntu OS. :D

---

