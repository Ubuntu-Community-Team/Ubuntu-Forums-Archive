---
title: "Wubi 10.04 in Windows 7 not working anymore"
date: 2010-11-09
forum: General Help
---

### Post by tommietje40 on 2010-11-09
Hi there,

I started using Ubuntu 10.04 about two months ago on my 64-bit i5 Sony Vaio with Windows 7 pre-installed, using only a C:\ partition. I've installed using Wubi, although at the time I wasn't aware of that.
For two months Ubuntu has been running perfectly, but overnight everything changed. This is what happens:

- I first get a screen where I can select either Windows 7 or Ubuntu. 
- I select Ubuntu
- Normally here i get a screen where I can select different Linux kernels. Now I get a Grub Error saying:
"[ Minimal BASH-Like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]"
grub>

I've already tried a couple of things, including changing the C:\wubildr file (since that was a know error for Wubi 9), but that didn't work. I got the same error but it now ended with grub:sh>

I also read somewhere on this forum that in C:\Ubuntu should be a folder disks. In my case I only have:

install (folder)
winboot (folder)
Ubuntu (pictogram)
uninstal-wubi (application)

I would just uninstall wubi and do a clean install from a liveCD, but the main problem is that I've used Ubuntu the last couple of weeks for school and there are some pretty important files on my Linux partition. Stupid of course, but I haven't made a back-up of those files...

Does anybody have an idea what to do?

Thanks!

---

### Post by Verbeck on 2010-11-09
not a fix for the issue, but you can follow the instructions at the [ubuntu wiki]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20the%20Wubi%20files%20from%20Windows?") to access the wubi files from windows

---

### Post by Hippytaff on 2010-11-09
It is normally recommended that Wubi only be used as a trial of ubunutu. If your happy with ubuntu it's recommended to to a 'real' Partition. I would suggest rescuing any files you need from wubi using the link in the previous post, and then set about doing a real partition.
 
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
 
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
 :-)

---

### Post by tommietje40 on 2010-11-09
Thanks for your quick reply's. I just have a problem trying to recover my Ubuntu files with those programs from the Ubuntu Wiki. The problem with this is just that it says to find the files in "c:\ubuntu\disks\, but I don't have that folder... Should I just consider my files lost or is there another way?

---

### Post by Hippytaff on 2010-11-09
Did you try this?
 
[https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won't%20boot]("https://wiki.ubuntu.com/WubiGuide#How%20can%20I%20access%20my%20Wubi%20install%20and%20repair%20my%20install%20if%20it%20won't%20boot")?

---

### Post by bcbc on 2010-11-09
Look for a hidden folder c:\FOUND.000 - something like that. 

Run check disk (My computer, rightclick on drive icon, Properties, Tools, Check disk for errors, Fix automatically) - will likely require reboot to check. 

The \ubuntu\disks folder shouldn't just disappear.

---

### Post by tommietje40 on 2010-11-09
Strange... I ran chkdsk /r in de Windows command prompt on C:, it did the check next time I rebooted. The system check ran (and took a very long time as well), but once in windows I can't find found.000 at C:, or when searching for it. I do show hidden folders...

---

### Post by bcbc on 2010-11-09
Search your whole computer for the file 'root.disk'. 

Did anything strange happen prior to the grub prompt thing?

---

### Post by tommietje40 on 2010-11-14
I solved it eventually by running chkdsk, but found.000 didn't appear in C:/ (I guess Windows 7 doesn't show that folder, even when viewing hidden files). So I booted from an Ubuntu 10.10 Desktop CD, here I could find the folder found.000 in C: on my Windows filesystem and root.disk was in here. I made a copy of it, and placed it in C:/ubuntu/disks (together with some other files). Ubuntu still didn't boot but I didn't get the same error anymore.
I decided to back-up the files I needed using explore2fs, uninstall Wubi and do a new clean instal on another partition using the Desktop CD. Everything works fine now.
Thanks for the help!

---

