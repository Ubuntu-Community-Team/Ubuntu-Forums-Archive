---
title: "Missing kernel"
date: 2011-05-16
forum: General Help
---

### Post by CurtisB on 2011-05-16
I am fairly new to ubuntu, and linux, my computer has windows 7 and I set it up to dual boot ubuntu, following the instructions on the ubuntu website. Recently my computer gave me a message saying it was full, so I deleted some unimportant files, one of which being a folder labeled "ubuntu" on my windows C:\ drive, which I thought was left over from an earlier failed attempt to install ubuntu. This file turned out to be a swap folder with very important information. After this I was not able to boot ubuntu anymore, and there was a missing "wubildr" file, which I was able to replace. The swap folder appears to be back to the way it was, but when I try to boot ubuntu I get a GRUB prompt and I am not able to locate the kernel. Could anyone point me in the right direction?

P.S. Sorry for the long explanation, I'm trying to get all the information I have out right away.

---

### Post by wojox on 2011-05-16
I don't know much about wubi, but I know someone who does [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198&highlight=wubi+megathread")

---

### Post by bcbc on 2011-05-17
> **CurtisB said:**
> I am fairly new to ubuntu, and linux, my computer has windows 7 and I set it up to dual boot ubuntu, following the instructions on the ubuntu website. Recently my computer gave me a message saying it was full, so I deleted some unimportant files, one of which being a folder labeled "ubuntu" on my windows C:\ drive, which I thought was left over from an earlier failed attempt to install ubuntu. This file turned out to be a swap folder with very important information. After this I was not able to boot ubuntu anymore, and there was a missing "wubildr" file, which I was able to replace. The swap folder appears to be back to the way it was, but when I try to boot ubuntu I get a GRUB prompt and I am not able to locate the kernel. Could anyone point me in the right direction?

P.S. Sorry for the long explanation, I'm trying to get all the information I have out right away.

I'm afraid you deleted the whole thing when you removed the C:\ubuntu folder. The virtual disk Wubi uses is \ubuntu\disks\root.disk and usually Windows won't place it in the recycle bin when it's deleted as it is too large. If you have some data recovery software you might be able to recover it if you stop using your computer, but if you've made changes since deleting there's a good chance that parts of it have been overwritten.

---

### Post by wildmanne39 on 2011-05-17
> **CurtisB said:**
> I am fairly new to ubuntu, and linux, my computer has windows 7 and I set it up to dual boot ubuntu, following the instructions on the ubuntu website. Recently my computer gave me a message saying it was full, so I deleted some unimportant files, one of which being a folder labeled "ubuntu" on my windows C:\ drive, which I thought was left over from an earlier failed attempt to install ubuntu. This file turned out to be a swap folder with very important information. After this I was not able to boot ubuntu anymore, and there was a missing "wubildr" file, which I was able to replace. The swap folder appears to be back to the way it was, but when I try to boot ubuntu I get a GRUB prompt and I am not able to locate the kernel. Could anyone point me in the right direction?

P.S. Sorry for the long explanation, I'm trying to get all the information I have out right away.
I have had problems close to yours with virtualbox and it sounds like it is just gone. I had to reinstall the os in my case.

---

### Post by CurtisB on 2011-05-31
Thanks for the help. If anyone was wondering, I ended up reinstalling. Lessons in maintaining proper backups suck.

---

### Post by dFlyer on 2011-05-31
Sometimes I wish they had a checkbox that needs to be checked requiring a person to make a backup of there important data before allowing a person to download the iso. Than again when they boot the install disk they had a checkbox again requiring backups before installing. I think that would solve 99% of the install problem when dual booting.

---

### Post by linuxinstalledfromhdd on 2011-05-31
I agree, users need to backup anything important before they start making radical changes to their existing systems. :P

---

### Post by glene77is on 2011-06-01
Curtis,
Always keep your "Created Data" in a different partition.  
I keep all mine on a different partition, in a folder named   "MY_" , with dozens of subdir inside. 
It is a simple thing to back-up that one subdir to my external HD. 

:)

---

