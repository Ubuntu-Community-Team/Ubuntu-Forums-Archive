---
title: "Grub issue?"
date: 2012-03-07
forum: General Help
---

### Post by PossumJenkins on 2012-03-07
I just installed Ubuntu 11.10 on my HP Pavillion g7.  My intention was to have it dual boot with Windows7 OS that was already present.  The Grub doesn't show up when I reboot and it goes straight to Ubuntu.  I cannot get to Windows at all.  When partitioning, I set the Linux partition as primary, which may have been a mistake.  how can I get access to Windows?  If all is lost, how can I get access to the files I have in the Windows partition?

---

### Post by sikander3786 on 2012-03-07
Welcome to the forums! :)

Press the <super> (Windows logo key) from the keyboard and search for and start 'Terminal'. Run these commands and post the outputs please:

```
sudo fdisk -l
sudo update-grub
```

The 'Terminal' would prompt you for the password but won't show any characters on the screen while you type it. Just feed your password and hit <Enter>.

If 'Windows' is listed in the output of the second command, it means that Grub has been configured and hopefully you would be able to dual-boot now. If Windows isn't there, you might need to post the output of bootinfoscript as per instructions here so that we can take a look and offer the solution:

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

But at first, please post the outputs of the above 2 commands. I posted the 'bootinfoscript' instructions as I doubt I might not be able to get back online till the evening so if you post those outputs, someone else might take a look and be able to advise you.

---

### Post by PossumJenkins on 2012-03-07
Here is the output of the commands:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7b74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   390627327   195312640   83  Linux

---

### Post by PossumJenkins on 2012-03-07
When attempting to perform boot script command, The return I get is: 'No such file directory'.

---

### Post by raja.genupula on 2012-03-07
give us terminal code , i mean what you have entered and what you got ? 

Thank you .

---

### Post by Cheesemill on 2012-03-07
If you only have one hard drive then you're out of luck, you have installed Ubuntu on the entire disk overwriting the Windows partition completely.

---

### Post by sikander3786 on 2012-03-07
> **PossumJenkins said:**
> Here is the output of the commands:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c7b74

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   390627327   195312640   83  Linux

This isn't the complete output I believe. Please try again and post the complete outputs of both the commands mentioned in my earlier post.

Thanks.

---

