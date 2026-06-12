---
title: "Dual Boot/  MBR issues!"
date: 2011-10-27
forum: General Help
---

### Post by bloodbruise on 2011-10-27
So two days ago i decided to install ubuntu for the first time. Everything seemed to go great, I installed it on my second hard drive and it was running good, updated it all, even installed a few programs to get used to using linux. 
 
After shutting my computer off, and turning it on, it later didnt want to start, kept loading from my disc, and if i took it out, it kept trying to recover my main install of windows 7.
 
I went in the bios and changed the boot order, then i guess what happened was in my install of ubuntu i changed the MBR (Master boot record) to i guess GRUB?
 
Not 100% sure but here is what i am now dealing with, i tried to fix the MBR and have it be the standard windows 7 MBR instead of grub, well when i did that i am now getting an error every time i start my laptop : Missing Operating System.
 
I have read on many forums and got the general idea that i needed to use my windows 7 installation disk and repair windows. So in repair windows you are then supposed to select windows 7 in the list of operating systems, mine doesnt show up.
 
It then tells me to load the drivers for my hard disk, how do i do that? or how can i even revert back to GRUB? preferably i DONT want Ubuntu to be my primary MBR.
 
Im really not sure what steps to take. If anyone needs to know what kinda of laptop i have to maybe find out my hard drive:
 
Asus G73-JH
500gb Sata Drive - Not sure what it is
 
I dont know what drivers i need to load to get windows 7 showing. When i get it showing i then want to make sure i have GRUB as an MBR but on my SECOND hard drive. They are currently labeled C for Windows and E for Ubuntu. 
 
Thanks for any help!

---

### Post by Sef on 2011-10-27
> I went in the bios and changed the boot order, then i guess what happened was in my install of ubuntu i changed the MBR (Master boot record) to i guess GRUB?


That is correct. GRUB will allow you the option of booting into both Windows and Ubuntu. Windows MBR will only allow you to  boot into Windows.

> I dont know what drivers i need to load to get windows 7 showing. When i get it showing i then want to make sure i have GRUB as an MBR but on my SECOND hard drive. They are currently labeled C for Windows and E for Ubuntu. 

Click on Dash Home > type Terminal in the search box > click on the Terminal icon > Copy and Paste this code in the Terminal: sudo fdisk -l > Copy and Paste the results here.

That will show what partitions you have and what is on them. GRUB should automatically give you the option of booting into Ubuntu (default) and Windows.

---

### Post by bloodbruise on 2011-10-27
As of right now i have NO MBR... I cant even see GRUB. I went to repair windows MBR and was told to open the CMD promt and type in bootrec/fixmbr.
 
That was supposed to fix my windows boot record and make it the MBR. So i was told, no i am left with a message telling me : Missing Operating System. I can use my win7 installtion disk and boot from that, but nothing else, as of now my hard drives are rendered useless. :confused:

---

### Post by bloodbruise on 2011-10-27
> **Sef said:**
>  
 Click on Dash Home > type Terminal in the search box > click on the Terminal icon > Copy and Paste this code in the Terminal: sudo fdisk -l > Copy and Paste the results here.
 
As of right now i have NO MBR... I cant even see GRUB. I went to repair windows MBR and was told to open the CMD promt and type in bootrec/fixmbr.

That was supposed to fix my windows boot record and make it the MBR. So i was told, no i am left with a message telling me : Missing Operating System. I can use my win7 installtion disk and boot from that, but nothing else, as of now my hard drives are rendered useless. :confused:

---

### Post by Mark Phelps on 2011-10-27
The fixmbr option doesn't repair the Boot, it only rewrites the MBR.

Since you appear to have a Win7 disk, reboot into it and run Repair Install -- three times.  Sometimes it takes more than one pass for it to actually work.  Also, your best source of Win7 technical info is the Windows 7 forum: sevenforums.com.  You should go there and check out their tutorials.  They have one listing the commands you should run from the Win7 disk to restore Win7 boot.

If the results of the fdisk command show the NTFS partitions still there, then at least you didn't reformat them.

So, boot from an Ubuntu desktop CD, use the Try Ubuntu option, go into the Home icon and see what is listed there.  If there is an entry for your Windows filesystem, click it -- and then see what files and folders exist in the Nautilus window.

---

### Post by bloodbruise on 2011-10-27
> **Mark Phelps said:**
> So, boot from an Ubuntu desktop CD, use the Try Ubuntu option, go into the Home icon and see what is listed there.  If there is an entry for your Windows filesystem, click it -- and then see what files and folders exist in the Nautilus window.

Yeah im going to have to try to boot from my flash drive which i installed ubuntu off of. Hopefully that will work just the same. I iknow i didnt reformat because when i go to load a driver using the windows7 installation disk i can still see my C drive with everything it had previously.


Ill try to see if i can boot from my stick, if i can, and i can get Ubuntu running can i fix it from their?

---

### Post by bloodbruise on 2011-10-27
> **bloodbruise said:**
> 
Ill try to see if i can boot from my stick, if i can, and i can get Ubuntu running can i fix it from their?


BTW this doesnt work. I cant boot from CD or disk, not for Ubuntu anyway... Not sure what i can do..

---

### Post by oldfred on 2011-10-28
If you have a bootable USB or CD you have to change BIOS or use one time boot key (some may require both) to boot. A few computers seem to need a full power off to totally reset.

If you can boot Ubuntu liveCD/USB run this:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Or download this which you can install from LIveCD or download its liveCD. It can run script and may make minor repairs.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

