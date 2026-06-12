---
title: "Which partitions do I delete after Ubuntu uninstall?"
date: 2011-07-18
forum: General Help
---

### Post by midamah on 2011-07-18
Hello everyone,

I'm a super newbie, and I am trying to fully uninstall Ubuntu..I did the windows 7 recovery bootrec.exe/fixmbr thing, then according to another thread on here, I would now have to delete partitons. I have no clue what partitions to delete. I've attached a photo of it, there are four partitions under volume that don't have names..so I'm confused.

**Picture of my partitions:**

[http://imgur.com/KvOzZ](http://imgur.com/KvOzZ)

p.s. I plan to reinstall it again, but using Wubi and also when the nvidia driver issue is fixed, because I couldn't use my dual boot at all because the screen went black.

Thank you for your time

---

### Post by akand074 on 2011-07-19
Windows can't see Ubuntu partitions. You'll need a separate partition manager that can handle EXT filesystems, or use the Ubuntu disc and boot into a live session to be able to see them and remove them (assuming they aren't already taken care of as you can only have 4 primary partitions and it seems yours is taken up, not sure what's going on there).

---

### Post by Wim Sturkenboom on 2011-07-19
Quite sure windows can see the partitions; it just can't read them. Not behind a dual boot at the moment to verify. Windows disk management should do the trick as far as I know.

---

### Post by midamah1 on 2011-07-19
> **akand074 said:**
> Windows can't see Ubuntu partitions. You'll need a separate partition manager that can handle EXT filesystems, or use the Ubuntu disc and boot into a live session to be able to see them and remove them (assuming they aren't already taken care of as you can only have 4 primary partitions and it seems yours is taken up, not sure what's going on there).

Thank you for answering me!

I've did as you said and am on gparted, but now that I see it, I don' t know what to do.lol I read somewhere that I needed to unmount the partition in order to delete it. But,  "umount" under "partition" is greyed out.

**here's a picture of my gparted**
[http://imgur.com/VABJ0](http://imgur.com/VABJ0)

I have no idea what most of that stuff is.

---

### Post by hhh on 2011-07-19
Everything ntfs is Windows, obviously don't delete those. Your Ubuntu partitions are ext4. The mounted partitions are the ones with key icons next to them, in this case 2 swap partitions. Unmount the bottom swap first, then the one above, then the extended partition (/dev/sda4). Then you can delete those partitions (/dev/sda4, sda5, 6, 7, eight).

---

### Post by mastablasta on 2011-07-19
or you can just delete them from windows (and then leave empty disk space or add it to windows disk). you can see the size of them in Ubntu so you can delete those with the same disk size from windows as they are not mounted by windows.
 
by the way what nvidia driver issue? proprietary driver or opensource driver?

---

### Post by midamah1 on 2011-07-19
> **mastablasta said:**
> or you can just delete them from windows (and then leave empty disk space or add it to windows disk). you can see the size of them in Ubntu so you can delete those with the same disk size from windows as they are not mounted by windows.
 
by the way what nvidia driver issue? proprietary driver or opensource driver?

NVIDIA GeForce 6150SE nForce 430

---

### Post by midamah1 on 2011-07-19
> **hhh said:**
> Everything ntfs is Windows, obviously don't delete those. Your Ubuntu partitions are ext4. The mounted partitions are the ones with key icons next to them, in this case 2 swap partitions. Unmount the bottom swap first, then the one above, then the extended partition (/dev/sda4). Then you can delete those partitions (/dev/sda4, sda5, 6, 7, eight).
OK, I followed your directions, but for some reason I'm not given the "unmount" option. Like for example I don't even see it under "partition" when I click on a swap file.

But, I do see it when I click on the /dev/sda5,7 but it's not clickable.

---

### Post by plucky on 2011-07-19
> **midamah1 said:**
> OK, I followed your directions, but for some reason I'm not given the "unmount" option. Like for example I don't even see it under "partition" when I click on a swap file.

But, I do see it when I click on the /dev/sda5,7 but it's not clickable.

Just turn swap off, there should be an option to do so for both linux swap partitions and then you should be able to delete all the partitions within the extended partitions and then the extended partition itself.

Then use windows disk management to give the space back to windows.


Good Luck

---

### Post by midamah1 on 2011-07-19
> **plucky said:**
> Just turn swap off, there should be an option to do so for both linux swap partitions and then you should be able to delete all the partitions within the extended partitions and then the extended partition itself.

Then use windows disk management to give the space back to windows.


Good Luck

I did it, I deleted the partitions, here's a picture of it:
[http://imgur.com/Pw9Eq](http://imgur.com/Pw9Eq)

and my last question, I promise..how do I give the space back to windows, in windows disk management? It seems like there should be a tutorial for people who have no clue about this stuff.lol

Thank you,
Mi

---

### Post by westie457 on 2011-07-19
From Gparted in a LiveCD session.

Select sda2 (your Windows Partition). Click on resize/Move. In the next window drag one end of the partition to the right as far as it will go. Click Continue. Click Apply and in the Warning Dialogue click Okay. Wait until process finishes.

**Do not stop it or interfere with it. You will have an unusable system.**. This applies to the above and the below.

In Windows.

Navigate your way to the location as shown in the first picture you posted.

Right-click on the partition for your C:\ drive. Select extend volume, choose how big you want it. Click okay. Wait until confirmation of finished process. All done.

---

### Post by midamah1 on 2011-07-19
> **westie457 said:**
> From Gparted in a LiveCD session.

Select sda2 (your Windows Partition). Click on resize/Move. In the next window drag one end of the partition to the right as far as it will go. Click Continue. Click Apply and in the Warning Dialogue click Okay. Wait until process finishes.

**Do not stop it or interfere with it. You will have an unusable system.**. This applies to the above and the below.

In Windows.

Navigate your way to the location as shown in the first picture you posted.

Right-click on the partition for your C:\ drive. Select extend volume, choose how big you want it. Click okay. Wait until confirmation of finished process. All done.

**THANK YOU all** for your prompt responses, and helpfulness! My problems solved. I truly appreciate it. I hope this thread will come in handy to others who have no clue what their doing, like me.

---

### Post by Wim Sturkenboom on 2011-07-19
In which case as suggest that you mark the thread as solved using the threadtools just above the first post on a page.

OOPS
I guess you forgot your password for the original user so that will not work

---

### Post by midamah1 on 2011-07-19
> **Wim Sturkenboom said:**
> In which case as suggest that you mark the thread as solved using the threadtools just above the first post on a page.

OOPS
I guess you forgot your password for the original user so that will not work

Yea, forestpiskie was pretty concerned about my "two" accounts. oh well.

---

