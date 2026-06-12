---
title: "Installing Ubuntu Problem"
date: 2012-08-27
forum: General Help
---

### Post by raja34766 on 2012-08-27
I have a disk of Ubuntu 11.04. I have windows xp on my hard disk C drive. I have 3 partitions namely C, D and E. Hard disk size is 1TB. I want to remove my windows xp and install ubuntu but I do not want to remove the partitions and the datas in my other drives like D and E. I only want to format xp completely and install ubuntu. I have read many articles from everywhere and became confused. So if someone can help me with this in step by step then it would be a real help.

Thank You.

---

### Post by spiky001 on 2012-08-27
Hi  Have  look at this guide  [http://www.dedoimedo.com/computers/ubuntu-install.html](http://www.dedoimedo.com/computers/ubuntu-install.html)

---

### Post by raja34766 on 2012-08-29
I do not want to dual boot the system.I just want to remove xp and install ubuntu though i do not want to remove the other drives or delete partitions

---

### Post by Bucky Ball on 2012-08-29
Could you post the result of:

```
sudo blkid
```... please?

Easiest? Boot from a LiveCD, launch Gparted, right click to make sure your Win partition is unmounted (is should be on sda, first partition and NTFS), delete. 

Expand your Ubuntu / partition, if that is what's next, into the free space you've created. You're done. 

Problem with this is you will be deleting grub if you have installed on that partition but easy enough to reinstall.

---

### Post by raja34766 on 2012-08-30
Please tell me what should i do step by step. I have never used ubuntu before.

---

### Post by mastablasta on 2012-08-30
> **Bucky Ball said:**
> Could you post the result of:
```
sudo blkid
```... please?
.
1. boot from live CD
2. open terminal and copy and paste this code in
3. copy and paste the output you get here.
 
Install in steps was already mentioned
> 
1. Boot from a LiveCD, 
2. launch Gparted, 
3. right click to make sure your Win partition is unmounted (is should be on sda, first partition and NTFS), 
4. delete [*it*]. 
5. Expand your Ubuntu / partition, if that is what's next, into the free space you've created. [if you need to expand it at all. leave it unformatted disk space]
6. You're done. 
[*7. begin with install*]
*[8. install to largest free disk space*]
 .
 
this is how install look like: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by raja34766 on 2012-08-31
If I use the option "Replace Windows Xp woth Ubuntu" then would I have to lose all the documents that I have in other drives like D and E or will it only format the C drive and install ubuntu?

---

### Post by Bucky Ball on 2012-09-01
Just launch Gparted from the LiveCD and kill the Win partition before you start. It will be NTFS file system, you can't miss it, and there's probably more than one, depending on you Win.

You could do the 'Replace Windows' option and, theoretically at least, that will leave all else untouched. I never trust automatic installs myself so I go for 'Something Else' and do it manually. 

Before commencing any of this you should fully prepare by backing up anything you don't want to lose just in case you screw up.

Good luck with it. ;)

---

### Post by raja34766 on 2012-09-02
But I do not know how to use that "something else" option. Whenever I tried to install ubuntu from that option I wanted something and ended up doing something else.

---

### Post by raja34766 on 2012-09-06
Is there anybody who can help me with this?

---

### Post by Bucky Ball on 2012-09-07
[https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning]("https://help.ubuntu.com/community/Partitioning%20issues?action=show&redirect=Partitioning")

That will tell you about the various partition types. I suggest you start digging and learn as much as you can about Gparted as that is what is used during the install to partition. Make a plan regarding how you are going to partition your disk then fire away. 

As I said, if you have everything backed up, who cares if you screw up? If you do, treat it as a lesson learnt and repeat procedure until you get it right. This you actually need to learn. We can help but we can't make you 'know'. That comes with doing. There is a ton of info and howtos online. Good luck. ;)

---

### Post by mastablasta on 2012-09-07
> **raja34766 said:**
> If I use the option "Replace Windows Xp woth Ubuntu" then would I have to lose all the documents that I have in other drives like D and E or will it only format the C drive and install ubuntu?
 
 
easiest way to avoid this is to use gparted, delete windows partition (os it's unformated disk space) and then during install chose to install on largest unformatted disk space.
 
otherwise you would need to partition it manually. partition / (=root) and /swap should be enough.
 
/root is like C: in windows and /swap is like pagefile in windows.
 
you can also create separate /home partition if you partition manaully (which is sort of like "My documents" folder in windows)

---

