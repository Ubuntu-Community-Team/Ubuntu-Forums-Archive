---
title: "can't access all of partition"
date: 2009-09-28
forum: General Help
---

### Post by Rhetoric Camel on 2009-09-28
Alright I have my main hdd set up into two partitions, one being the c drive that windows is on (about 50gb dedicated to it) and the other drive (G) which is the drive ubuntu is on (about 250gb) I have also saved a lot of things from when I used windows on the G drive, but it seems all that stuff I cannot access at all through Ubuntu, how do I view this stuff? I have a bunch of movies I want to burn onto dvd's but I can't because for some reason I can't see/find them.

---

### Post by Giblet5 on 2009-09-28
If you told the Ubuntu installer to install onto the second disk partition, then I have bad news for you... Your G: drive is gone and non-recoverable. It has been overwritten.

I hope that's what you expected to hear.

Now, if you can still see G: from Windows, then you probably just need to mount it to see it under Ubuntu.

What is the output of ```
sudo fdisk -l
```

---

### Post by Rhetoric Camel on 2009-09-28
> **Giblet5 said:**
> If you told the Ubuntu installer to install onto the second disk partition, then I have bad news for you... Your G: drive is gone and non-recoverable. It has been overwritten.

I hope that's what you expected to hear.

Now, if you can still see G: from Windows, then you probably just need to mount it to see it under Ubuntu.

What is the output of ```
sudo fdisk -l
```

No it still works fine under windows, here's what I get from that code
```

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6cdf6cd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       38913   261369517+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe794ac88

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    7  HPFS/NTFS

```

---

### Post by Giblet5 on 2009-09-28
OK... Whew! I though maybe you blew away that second partition!

So you're running Ubuntu from an NTFS partition.

You should be able to just automount them from Nautilus.

When you click on Places/Home Folder, over on the left, you should see your Windows partitions even if they aren't mounted. Click on one and it should mount automatically and allow you to manage files in the usual way.

---

### Post by Rhetoric Camel on 2009-09-28
> **Giblet5 said:**
> OK... Whew! I though maybe you blew away that second partition!

So you're running Ubuntu from an NTFS partition.

You should be able to just automount them from Nautilus.

When you click on Places/Home Folder, over on the left, you should see your Windows partitions even if they aren't mounted. Click on one and it should mount automatically and allow you to manage files in the usual way.

That's what I was thinking, but all I see is: rhetoriccamel, desktop, file system, network, 52.4Gb Media (the C drive), Second HDD (Which is my F drive, a separate hdd) and Trash. I know the G: drive still has all my other stuff on it because programs I use in windows run off of that drive and a movie I just recently watched in windows was also saved on the G: drive. No idea why it's not showing up, I don't really know a lot about Linux/Ubuntu but I figured it should show up on the side there like you said.

---

### Post by Rhetoric Camel on 2009-09-28
it seems when I look at "File System's" propeties it shows the full drive that should be accessible but I can't get to any of the files saved on there... very odd and kind of crappy.

---

### Post by Rhetoric Camel on 2009-09-28
alright a little more looking around on the forums and I found an answer, so this is solved....


in case anyone else is having this issue and you can't get it to work, open up Places>Home Folder (or any folder really) and in location switch to, if you're not already on this setting, to Text-Based Location Bar and type in
```
/host
```
that has given me access to all my saved files on the same drive that Ubuntu is running on. This has just saved me some extra rebooting into windows time and made it just one less thing I need windows for.
And as I was typing this I noticed if I just go into "File System" there is a folder called "host" which is the same thing... sorry, stupid me. I've been at this for about 3 days now, of course it was this easy.


Thanks for trying to help Giblet5.

---

