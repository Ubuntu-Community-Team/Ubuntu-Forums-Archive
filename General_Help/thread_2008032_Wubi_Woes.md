---
title: "Wubi Woes"
date: 2012-06-21
forum: General Help
---

### Post by Aeighty on 2012-06-21
Problem in point form : 

1. Installed Ubuntu using Wubi ( first mistake ) 
2. Did system restore to factory settings 
3. installed Ubuntu 12.04 LTS ( 64 bit version ) via DVD to a separate partition on HDD 
4.Reboot, get option to run Ubuntu or Windows from GRUB, run Ubuntu everything       works  
5.Reboot, this time run Windows get second option to boot Windows or Ubuntu.
6.Boot Ubuntu and get this error - File:\ Ubuntu\winboot\wbildr.mbr, application is missing or corrupt. 

Question: 

Was all of Wubi removed when doing the system restore leaving only the boot loader option behind ? I am assuming it was beacause i have found no trace of Ubuntu or Wubi files in C:
How can i remove this boot option assuming there is no ubuntu left on the windows partition and will it affect my current installation of Ubuntu ( on its own partition ) 

thanks very much. I have and am reading the Wubi sticky as i type this.

---

### Post by wilee-nilee on 2012-06-21
The ubuntu in the windows boot menu would not run.

Is the windows booting?

---

### Post by JKyleOKC on 2012-06-22
The second option you got at point 5 comes from a Windows file that was called "boot.ini" in WinXP but I believe has a different name in more recent versions. Since this file runs before Windows loads, the "restore to factory settings" apparently failed to replace it.

It's a plain text file, so you can edit it with Notepad or a similar text editor once you manage to locate it. It's in the root directory of the C: drive. Just delete the line that refers to the "wbildr" file and save the file. Do NOT change anything else in the file or you may find Windows refusing to boot at all...

---

### Post by Aeighty on 2012-06-24
Thanks for the reply guys.  jKyleOKC you say that it is just a text file that i can edit which is what i was hopping to hear thank you. 

and to answer other questions yes Windows boots fine its just the leftover Option to boot Ubuntu from the windows that is my issue. 

I will see if i can locate the file and delete it.

---

### Post by JKyleOKC on 2012-06-24
In XP, the file is hidden, so you may have to enable showing hidden and system files in order to find it. In XP, there's a heading "[Operating Systems]" about 3 or 4 lines up from the end of the file, followed by one line for each system to display on the menu. You want to make it so that there's only one such line, and it's the one for Windows.

---

### Post by Aeighty on 2012-06-27
Thanks for the help all is well. Now I can boot straight into windows from GRUB.

---

### Post by JKyleOKC on 2012-06-27
Good to hear! Please mark the thread solved as described in the link in my sig.

---

