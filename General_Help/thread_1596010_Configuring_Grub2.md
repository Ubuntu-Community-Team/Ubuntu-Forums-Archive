---
title: "Configuring Grub2"
date: 2010-10-13
forum: General Help
---

### Post by cloud2dream on 2010-10-13
Hi. I was hoping somebody would be able to help me with this:

I've got Windows XP, Windows 2000 and Karmic installed on the same HDD

2K and Karmic are in primary partitions and XP is in the first logical partition

I'm trying to get Grub2 to show options for XP and 2000 separately rather than the NT/2000/XP loader that goes into NTLDR. Everything I have tried so far either goes to the default in NTLDR or crashes one version of windows.

I was hoping to avoid having to use NTLDR as my boot manager and go directly from Grub2 to starting Windows, so any help would be very much appreciated.

Thanks

James

---

### Post by Quackers on 2010-10-13
Welcome to ubuntuforums :-)
Please go to the site below and download the boot script file to your desktop then run the command given on that site in a terminal. This will generate a results.txt file on your desktop.
Copy the contents of that file and in your next reply click on New Reply then click on the # symbol in the top bar then paste the file contents between the code tags.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by cloud2dream on 2010-10-16
Thank you. 

The bootscript showed me what I needed to change. Rookie mistake!

Cheers

James

---

