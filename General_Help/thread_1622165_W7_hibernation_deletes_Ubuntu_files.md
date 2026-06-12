---
title: "W7 hibernation deletes Ubuntu files"
date: 2010-11-15
forum: General Help
---

### Post by wgarn on 2010-11-15
I am using Windows 7 and Ubuntu on the same computer. I 
have a shared partition, which is accessed in Ubuntu via &#8220;/media/Data&#8221; and in Windows 7 via &#8220;d:\&#8221;. Normally I hibernate Windows 7 and resume working in [COLOR=#366388]Ubuntu[/COLOR] (which I restart - because of its speed). I have used swriter and Matlab (under Ubuntu) to write several documents, functions and saved them. 
No problems so far. I resumed Windows 7 - all my work has disappeared! I have looked for deleted files, hidden files and searched the partitions to find the files. I have still records of indicating that it was a recent document or that I called functions. What has happend? 
This mysterious behaviour is reproducible!
1. Start W7 
2. Create folder and file: &#8220;D:\test\W7file.txt 
3. Hibernate W7
 
4. Start Ubuntu
5. W7file.txt survived hibernation.
6. Create /media/Data/test/UbuntuFile.txt
7. Shut down Ubuntu
 
8. Resume W7
9. Note: UbuntuFile.txt has disappeared!
Technicalities: W7 Enterprise Edition (latest version), Ubuntu 10.10, shared 
partition has NTFS
 
Does Ubuntu or Open Office keep safety copies of recent files somewhere?

---

### Post by TeoBigusGeekus on 2010-11-15
After step 9, have you tried booting Ubuntu again? Is the file still there?
Have you tried ending windows' hibernation and rebooting?

---

### Post by Ophidion on 2010-11-16
Hi, all. I have a dual boot system of both vista and ubuntu. I installed ubuntu for trial then I found it better than vista. I hibernated vista 4 days ago through which i didn't feel I want to see it again. I gathered 1.5 GB of deb and how to files put them on a shared ntfs drive. After I decided to erase the buggy windows system and go on a new life with ubuntu I resumed vista to collect some of my personal files and settings and to say good by. !! Aaahhh !! where are the 1.5 GB of deb files and how to. 4 days work just disappeared so as to give me a bad memory of vista and the whole windows system. I searched there and there, tried recovery software and no hope. I found files that I deleted from ubuntu on that ntfs drive are back again!! How I deleted them system gave a message of can't delete. then after a restart a check desk appeared during booting to vista I left it to go on and the files were recovered again. Thanks god. I was panic so that I bought a USB external disk to back up. I am intending now to format and repartition the whole disk to go on with ubuntu and xp (just because of a couple of games I liked works in it and failed to load in a virtual machine environment).

---

