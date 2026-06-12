---
title: "put home directory on windows partition"
date: 2011-10-01
forum: General Help
---

### Post by epic.mint on 2011-10-01
Im thinking of making an Ubuntu dual-boot on a laptop with a 40GB harddrive so im wondering if i could put my home directory inside a windows partition.  making it accessible to both operating systems

---

### Post by LowSky on 2011-10-01
no.. short answer is it would lead to permission issues.
but you can read form windows if needed. see this [http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

---

### Post by prodigy_ on 2011-10-01
[removed, double post]

---

### Post by prodigy_ on 2011-10-01
You can mount an NTFS partition as your Documents folder (that's pretty much what I've been doing for a long time now) but there are certain limitations.

First, if you just want to mount a partition as ~/Documents, it should be a clean partition, not a partition where Windows is installed. If you have only one NTFS partition, you'd better mount it elsewhere and replace ~/Documents directory with a symbolic link to My Documents folder from your Windows account.

Second, Linux ntfs-3g driver doesn't honor Windows filename restrictions. If you're not careful you can end up having files that Windows is unable to handle on your shared partition.

---

### Post by Morbius1 on 2011-10-01
> Second, Linux ntfs-3g driver doesn't honor Windows filename  restrictions. If you're not careful you can end up having files that  Windows is unable to handle on your shared partition.     Yes and no.

You can mount the ntfs partition such that it won't allow you to save from Linux a file with a name that Windows cannot handle.

For example, if you mounted your Windows partition like this:
> UUID=DA9056C19056A3B3 /mnt/WinC ntfs defaults,uid=1000 0 0Then you might end up saving a file that Windows cannot read. But if you add one more option:
> UUID=DA9056C19056A3B3 /mnt/WinC ntfs defaults,uid=1000,[COLOR=Blue]**windows_names**[/COLOR] 0 0Then it will prevent you from saving odd named files.

---

### Post by prodigy_ on 2011-10-01
> **Morbius1 said:**
> windows_names
Heh. Checked the changelog - they added it about a year ago. That's what get I for not paying attention. :)

---

### Post by Mark Phelps on 2011-10-01
Don't mount ANY of your Windows OS partition, regardless of what it contains, in read-write manner.  Doing so is asking for problems down the road.

If you have files in your Windows documents folder you want to use in Ubuntu, then create an NTFS format shared DATA partition (not OS partition) and use that.  That will avoid any filesystem corruption issued that could later render Windows unbootable.

---

### Post by Basher101 on 2011-10-01
> Don't mount ANY of your Windows OS partition, regardless of what it contains, in read-write manner. I have done this many times reading documents on my desktop folder and writing some there...i have not expirienced any problem whatsoever. I have a shared 400GB storage partition, but im too lazy moving all the small fries.

---

### Post by prodigy_ on 2011-10-01
> **Mark Phelps said:**
> Doing so is asking for problems down the road.
Not exactly. Can't recall if there were any issues with XP but I'm sure I've had none with Win7. Even non-English filenames are recognized correctly (much to my surprise as I'm too used to all kinds of codepages/encodings incompatibility).

---

### Post by WasMeHere on 2011-10-01
> **Morbius1 said:**
> Yes and no.

You can mount the ntfs partition such that it won't allow you to save from Linux a file with a name that Windows cannot handle.

For example, if you mounted your Windows partition like this:
Then you might end up saving a file that Windows cannot read. But if you add one more option:
```
UUID=DA9056C19056A3B3 /mnt/WinC ntfs defaults,uid=1000,[COLOR="RoyalBlue"]windows_names[/COLOR] 0 0 
```
Then it will prevent you from saving odd named files.

Thanks, this is really useful!

Yet, I agree with *Mark* that is is a good idea to use a *data* partition available from both linux and windows. Symbolic links can be used so that it is convenient to get there from the regular locations of documents and media files.

---

