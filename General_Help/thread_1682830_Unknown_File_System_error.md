---
title: "Unknown File System error"
date: 2011-02-06
forum: General Help
---

### Post by hermanj04 on 2011-02-06
Hello,
 
I was attempting to install ubuntu 10.04 Netbook edition alongside Windows 7 Starter on my netbook. After completing the installation, I receive this message every time I try to boot:
 
> error: unknown filesystem.
grub rescue>
 
Can anyone help me figure out how to get to either of the operating systems?

---

### Post by Rubi1200 on 2011-02-06
Hi and welcome to the forums :-)

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by hermanj04 on 2011-02-08
I tried all Saturday night and Sunday morning to get the computer to boot from the CD and couldn't get to it.  Then, as I was trying something else last night, it randomly booted from the CD.  It showed that Ubuntu had not installed into the unpartitioned space, so I reinstalled Ubuntu last night and it seems to be running fine now.

Thank you for trying to help.

---

### Post by Rubi1200 on 2011-02-08
Excellent! Glad you got things sorted out :-)

If you need more help with anything, just ask.

---

