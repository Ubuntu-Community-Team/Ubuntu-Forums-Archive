---
title: "Just installed Ubuntu dual boot. Why can I see all my Windows files!?!?"
date: 2009-09-06
forum: General Help
---

### Post by bridgetothesun on 2009-09-06
I installed Ubuntu 9.04 as a the second OS on my computer. The other is Win XP. 

The scary thing for me is that I can see all my Windows related files while in the Ubuntu OS Place. Why is that and how can I keep my delicate windows files and settings away from my activities on Ubuntu?

Is this normally supposed to work this way? I do not mind sharing my documents in Windows with Ubuntu, but the very windows specific settings and files that are critical to the OS should not be able to be accessed via Ubuntu. Or maybe I'm missing something?

Thanks.

---

### Post by Dr Belka on 2009-09-06
if you dont mess with that partition, it will be fine.

If you are that worried than just unmount the drive

---

### Post by Bucky Ball on 2009-09-06
If you have the files on a disk Ubuntu recognises, it will see the files. It is probably NTFS or FAT, right?

Just don't touch them. If you are talking about MS operating system files, they are not going to mean much to Ubuntu anyway. No biggie.

Think of it this way: Windows doesn't understand EXT3 partitions without some massaging. Therefore if you work on something in Ubuntu and then want to access it from Windows you are sweet. Just drop it somewhere on the Windows drive. 

A lot of people set up a FAT or NTFS partition specifically to share files between the two OSs. Common.

---

### Post by bridgetothesun on 2009-09-06
To first reply:

I'm sorry, I'm very new to Linux. 

Could you explain to me what exactly is happening with the partition and whatnot.

And what would I unmount? The windows part of the drive?


To second reply:

Yes I believe my Windows partition is setup as NTFS.

On a side note, I downloaded a game in a compiled linux format and want to extract it to the Games directory. However, in my OS Space I cannot find "Games" anywhere. Any help?


Thanks.

---

### Post by Dr Belka on 2009-09-06
right click on the partition's icon on your desktop and then click unmount


This will take the windows section of your hard drive "off" of the file system.  Of course if you want to see documents you made on linux, you need to store them in your windows partition as BB said

---

### Post by Bucky Ball on 2009-09-06
Why would you want to unmount it? It is not actually doing anything unless you do something with it. :)

---

### Post by Dr Belka on 2009-09-06
> **Bucky Ball said:**
> Why would you want to unmount it? It is not actually doing anything unless you do something with it. :)

yeah, man, If you dont go messing with the files yourself, it will be fine

---

### Post by bridgetothesun on 2009-09-06
Thanks for the replies. I do not have the partitions icon on my desktop. In fact I can't find it anywhere.

---

### Post by Bucky Ball on 2009-09-06
You can drag one from 'Places' or send one to the desktop from a file browser! (Not that you want to).

Just thought of it:

Open a terminal (Applications->Accessories->Terminal) and paste this in:

nautilus

That opens a file browser as root. Now, in the column on the left at the bottom, you should see a list which equates to 'Places' with your Windows partition there. Right click and delete it from the list in the left column.

---

### Post by bridgetothesun on 2009-09-06
Thanks. "Places" does not have the partition icon. I did a search and a ton of files came up. Is there a specific place I should look?

---

### Post by oboedad55 on 2009-09-06
> **bridgetothesun said:**
> Thanks. "Places" does not have the partition icon. I did a search and a ton of files came up. Is there a specific place I should look?

It may be under "Places/Removable Media".

---

### Post by Bucky Ball on 2009-09-06
You can drag one from 'Places' or send one to the desktop from a file browser! (Not that you want to).

Just thought of it:

Open a terminal (Applications->Accessories->Terminal) and paste this in:

```
sudo nautilus
```That opens a file browser as root. Now, in the column on the left at the bottom (bottom half under the line), you should see a list which equates to 'Places' with your Windows partition there. Right click and delete it from the list in the left column.


* Ooops! Posted twice sorry! Something strange happened. :-k

---

### Post by Dr Belka on 2009-09-06
is there a listing in places that says something like "26.2 GB media" or "OS" or something like that?

---

### Post by alphacrucis2 on 2009-09-06
> **bridgetothesun said:**
> Thanks. "Places" does not have the partition icon. I did a search and a ton of files came up. Is there a specific place I should look?

Odd. I thought you were saying earlier you could see it? Anyways under places menu you should see an icon that indicates the partition size followed by the word Media. Ubuntu doesn't normally mount NTFS partitions unless you ask it to, or add a permanent entry in your /etc/fstab file. If you click on the media icon the system should ask you for the your password and the partition should then be mounted until you manually unmount it or log out.

---

### Post by Bucky Ball on 2009-09-06
Post #12 will get rid of anything in 'Places'. :)

---

### Post by bridgetothesun on 2009-09-06
In Places I see "OS". Is that the same thing as "partition"?

This community is great. Even for an ignorant newbie like me...so much help!

I appreciate it!

If I restart, "OS" disappears from the desktop. I have to reenter my password for it to appear on the desktop again. Is this for security reasons?

Thanks.

---

### Post by bridgetothesun on 2009-09-06
Ahhh I think I'm getting it. When I enter the password I am effectively mounting my Windows partition, that's why I can see all the files. 

Interesting...

---

### Post by 3rdalbum on 2009-09-06
> **bridgetothesun said:**
> If I restart, "OS" disappears from the desktop. I have to reenter my password for it to appear on the desktop again. Is this for security reasons?

Yes, it's just part of the Linux security system.

It's kinda funny, most people are delighted that Ubuntu allows such easy mounting of their Windows drive :-)

---

### Post by Bucky Ball on 2009-09-06
> **3rdalbum said:**
> 
It's kinda funny, most people are delighted that Ubuntu allows such easy mounting of their Windows drive :-)

I was going to mention that before ... :)

Yea, bridgetothesun, you're getting it. There is a learning curve but that's not to say it isn't a fun ride!

---

