---
title: "Hard Drives, Ownership, Copying information."
date: 2010-01-15
forum: General Help
---

### Post by Nugar on 2010-01-15
Hi all,

I'm building a new system, with the goal of making it an Ubuntu-only box. Among the things I have installed, I have a 1tb ext4 hdd and a 320gb ntfs hdd.

Due to my ignorance, right now, I can't boot, but that's not the point of the question. Let me try to explain the situation:

Right now, the 1tb hdd has Ubuntu installed. And the 320gb hdd is just a drive for stashing stuff. (It used to be the "large" drive).

But what I want to do now is:

[LIST]
[*]Copy all the contents of the 320gb to the 1tb
[*]Format the 320gb as ext4 and install Ubuntu there so it is the "main" drive
[*]Re-format the 1tb as ext4 too to use it as the storage area
[/LIST]
But, when I try to copy the stuff from 320 to 1tb, I can't due to permission issues (I'm booting the box from the live CD).

So I sudo and the files are copied.

Now, when I try to verify (still booted from the LiveCD as the box itself doesn't boot yet) I'm told that I can't see the contents of the directories I just copied.

So the question is when I finally copy all the stuff I want to the 1tb, and install Ubuntu, will I be able to read the contents of those directories? I mean, not as root but as my regular user, or conversely, just doing a chown -R myuser:myuser <directory> would allow me to use the files normally?

Thanks in advance for any information regarding this.

---

### Post by oldos2er on 2010-01-15
Yes, running sudo chown -R user:user /media/whatever after you've installed Ubuntu on the 320GB drive will allow your user access to all files, as you said. You may need to mount it as root first.

---

### Post by audiomick on 2010-01-15
When you are shovelling stuff around from the live cd, it might make your life easier to go to the terminal and do
```
gksu nautlius
```
This will open a file manager with root priviliges. You should be able to copy anything anywhere, and look to see that it has got there.

You will have to then sort out your permissions when you get the machine booting.

---

### Post by mdshann on 2010-01-15
> But what I want to do now is:

    * Copy all the contents of the 320gb to the 1tb
    * Format the 320gb as ext4 and install Ubuntu there so it is the "main" drive
    * Re-format the 1tb as ext4 too to use it as the storage area

I would make sure that the last step comes before the first step... Reformatting the 1TB HDD after backing up your data to it would result in data loss.

---

### Post by Nugar on 2010-01-15
> **audiomick said:**
> When you are shovelling stuff around from the live cd, it might make your life easier to go to the terminal and do
```
gksu nautlius
```This will open a file manager with root priviliges. You should be able to copy anything anywhere, and look to see that it has got there.

You will have to then sort out your permissions when you get the machine booting.

Thanks audiomick and all. This is a great snippet of info!

---

### Post by Nugar on 2010-01-15
> **mdshann said:**
> I would make sure that the last step comes before the first step... Reformatting the 1TB HDD after backing up your data to it would result in data loss.

Hi mdshann,

Yes, What I meant was, after installing the OS on the 320gb, copy back the info there while I reformat the 1tb.

Cheers,

---

