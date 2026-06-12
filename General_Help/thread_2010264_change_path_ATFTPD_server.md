---
title: "change path ATFTPD server"
date: 2012-06-25
forum: General Help
---

### Post by aniceto pastrana on 2012-06-25
Hi everyone; 

I have installed the ATFTPD Server. The tfttp server works correctly and saves the files in the especified folder.

Else; I need that these files will be stored in a folder on a USB memory. For it; I run this commands:

# cd /media
# mkdir usb
# mount /dev/sdb1 /media/usb
# chmod 777 /media/usb

Then; I edit the atftpd file and in the path to save the files; i write "/media/usb/".

Now; whe I try to upload a file; I obtain this error: TFTP 2 Error: Access Violation.

I restart the pc without resolve the problem.

Do you help me; please?


Thanks a lot.

Regards.


Adrián.

---

