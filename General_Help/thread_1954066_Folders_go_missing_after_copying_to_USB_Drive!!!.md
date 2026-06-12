---
title: "Folders go missing after copying to USB Drive!!!"
date: 2012-04-07
forum: General Help
---

### Post by Avinash.Rao on 2012-04-07
Hi,

Dual Boot. 
Windows 7 Home Premium 64-bit Edition of Dell Inspiron Laptop. I have also installed Ubuntu 11.10 with dual boot option. In Ubuntu, the windows drive gets detected automatically and I backed a particular folder from the windows partition to an external USB drive.

The next time I rebooted the computer, many folders within the backed-up folder went missing! It is not there even in the USB drive. I booted to windows and checked the disk for errors during boot. It did a few things like deleting index entries, etc...The hard drive is clean and has no bad sectors. But the folders were still missing.. 

How do I restore these folders?

Thanks.

---

### Post by 2F4U on 2012-04-07
Just a guess, but did you safely remove the usb drive before unplugging it? Since writes to a usb drive happen asynchronously, just unplugging may leave you with an inconsistent file system on the usb drive.

---

### Post by Avinash.Rao on 2012-04-07
Yes I did. I found a solution. Windows 7 has option of restoring the previous versions of the the file if "Windows Protection" is enabled on NTFS partition. 

This can be achieved by right clicking on a folder and selecting the previous version you want to restore. I did this and was able to restore most of the files except few. The missing folders were created long ago and strangely, they were not present in the recent history!



> **2F4U said:**
> Just a guess, but did you safely remove the usb drive before unplugging it? Since writes to a usb drive happen asynchronously, just unplugging may leave you with an inconsistent file system on the usb drive.

---

