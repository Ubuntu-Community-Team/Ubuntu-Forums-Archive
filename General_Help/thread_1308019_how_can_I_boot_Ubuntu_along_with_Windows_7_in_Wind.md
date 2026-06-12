---
title: "how can I boot Ubuntu along with Windows 7 in Windows Boot Manager instead of GRUB?"
date: 2009-10-31
forum: General Help
---

### Post by charming on 2009-10-31
Hello.
 
I used to run ubuntu along Windows XP with Windows Boot Manager.
but now..
 
I Installed Windows 7 and then ubuntu 9.10, the GRUB boot was horrible so I repaired
Windows 7 in order to restore Windows Boot Manager or that what I thought it should be.. but I've failed.
 
ubuntu 9.10 is gone at the moment, I don't want to restroe ubuntu with GRUB anymore as much as I want the both of them in Windows Boot Manager.
 
thanks in advance.

---

### Post by charming on 2009-11-01
up.. may someone answer the most difficualt question ever. ;_;

---

### Post by Zoot7 on 2009-11-01
This might be of interest to you:
**[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5")**
And also this: Revert Karmic back to Grub Legacy
**[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18]("http://ubuntuforums.org/showpost.php?p=8071880&postcount=18")**

---

### Post by charming on 2009-11-01
oh btw; I'm runing two harddisk, Caviar Black 500GB for Windwos, Seagate 160GB for ubuntu (strangly I don't see ubuntu 9.10 in anywhere when I check them through Windows O_o).
 
not sure if that gonna change anything, but I'll try and report
 
thanks :D

---

### Post by charming on 2009-11-01
I tired this one 
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=5)
 
and I failed 'cuz [EXT2IFS]("http://www.fs-driver.org/") doesn't supports Windows 7
 
also.. I can't find where I installed ubuntu 9.10 in? 
I want to re-install -.-;
 
can someone tell me how to delete the current ubuntu 9.10?
 
I have 3 partions (two phyisc harddisks), the 1st hard is NTFS and 2nd is exFAT
yet I don't see anything on my 3red partion which supposed to installed there. ;)
 
Windows 7 installed in the 1st Harddisk, the NTFS one.
 
thank you in advance

---

### Post by Zoot7 on 2009-11-01
IMO you'd be better off you took the Jump and used Grub instead of the Windows bootloader it's much more efficient and easy to set up - Even Grub 2.

Either that, or just specify which hard drive you want to boot off in the BIOS, that way neither OS will ever interfere with each other as regards booting. ;)

---

### Post by goldencako on 2009-11-01
I'm not sure it works in Windows 7, but it works in XP and Vista. This is out of the top of my head, so the exact names might be a bit off. I will limit myself to explaining how to get rid of your Linux through Windows.

Go to Run then open diskmgmt.msc

A little window will pop up with your partitions and hard drives. You should look for one that says Healthy Unknown partition or something of the sort. Quick format it to FAT32 if possible (or exFAT). This will REFORMAT YOUR LINUX PARTITION. Be sure it's NOT your Windows partition or exFAT partition. It is very clear from their names which one is which, but be careful.

Anyways, with this done, if you wanna keep your Ubuntu, plug in the cd and reinstall the OS. My advice to you is to keep the GRUB.

I hope it helps.

---

### Post by philinux on 2009-11-01
To boot linux with vista or win7 without grub you need easybcd. Only for win7 you would need the latest version 2.0 beta. 

[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

---

### Post by charming on 2009-11-01
okay.. okay.. okay.. I decided to try the huge "Jump" and use GRUB instead of Windows Boot Loader. but now I want to delete the current ubuntu 9.10
 
here's a screenshot of my partions. as goldencako's idea to delete.
[http://img263.imageshack.us/img263/9158/are.png](http://img263.imageshack.us/img263/9158/are.png)
 
I don't know which one to format ;)
 
thank you :)

---

### Post by goldencako on 2009-11-01
From the looks of that image, there's no Linux around! The diskmgmt.msc should show *everything* on your computer. I suggest you do some adding up of memory to see if all the partitions/drives are actually showing. The Linux partitions should show like the second partitions [[COLOR="Blue"]here[/COLOR]]("http://i156.photobucket.com/albums/t8/italianxmna89/diskmanagement.jpg"). If you can't get it to appear on Windows, pop in the Live CD, start the installation process and choose to se up your partitions manually. It is generally pretty straight forward, and the partition manager is informative about what OSes are installed, however, don't do anything you're not sure about.

---

### Post by charming on 2009-11-02
ah the green one.. there were some green free spaces I deleted eailer.. didn't know those belong to ubuntu 9.10 lol
 
but those were in 500GB which aren't FAT and not supposed to be there.
 
how do I select where I want to install ubuntu 9.10 exactly?
 
I want to install ubuntu in the 2nd harddisk (160GB) which are FAT, not 500GB or 1TB.
 
 
BTW: I can viwe *System Reserved* when I boot from Live-CD but not from Windows 7. 
does that mean anything?
 
[http://img263.imageshack.us/img263/9158/are.png](http://img263.imageshack.us/img263/9158/are.png)

---

### Post by charming on 2009-11-02
okay.. okay..
 
all solved.
 
thank you very much! ^-^

---

### Post by goldencako on 2009-11-02
Good stuff. Booting through GRUB2?

Oh, and it would be nice of you to mark the Thread as SOLVED. To do that, just go to Thread Tools and click on the appropriate button. Thanks!

---

