---
title: "Installation Error in Ubuntu 11.04"
date: 2011-06-12
forum: General Help
---

### Post by asad.baig on 2011-06-12
Howdy!!
I'm trying to install **UBUNTU 11.04** from **WUBI** but installation ends with an error attached with the post. I have Dell Inspiron 1564 with Windows 7 Ultimate 64 Bit.
The procedure i have tried until so far is that i have downloaded Ubuntu 11.04 from [http://www.ubuntu.com/download/ubuntu/download]("http://www.ubuntu.com/download/ubuntu/download") and then i have copied the *.ISO File* in the desired local drive where i want to install my Ubuntu. Secondly, i have downloaded WUBI from [http://www.ubuntu.com/download/ubuntu/windows-installer]("http://www.ubuntu.com/download/ubuntu/windows-installer") and followed the procedure as mentioned but it ended with an error quoted in the attachments.
I have also tried to reboot the system to check whether UBUNTU 11.04 loads at the Boot Manager but it failed. 

**HELP ME!!**

---

### Post by bcbc on 2011-06-12
It seems like D: is a Windows dynamic drive. Don't install Ubuntu (Wubi or not) on dynamic drives. 

You can check by going to Windows' "Disk Management"

---

### Post by asad.baig on 2011-06-12
Thanks! I have seen my drives from DISK MANAGEMENT and the screen shot is attached in the post.
Can anyone please tell me how to Convert the drives from **DYNAMIC** to **BASIC** without losing the data within ago because i'm eager to install UBUNTU 11.04 which has proved that YES!! Big ideas do come in small packages.

---

### Post by bcbc on 2011-06-13
See this thread for some ideas on converting from dynamic drives: [http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)

However, please be aware that all the guides say there is a chance of data loss - so it's best to back up everything completely before attempting this.

If you're just trying out Ubuntu you could always use a live USB or a virtual machine (e.g. vmware or virtual box) - and then if you decide you want it permanently then go to the trouble of converting.

Hope that helps!

---

