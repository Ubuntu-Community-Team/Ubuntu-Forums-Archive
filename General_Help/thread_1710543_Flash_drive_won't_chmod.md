---
title: "Flash drive won't chmod?"
date: 2011-03-20
forum: General Help
---

### Post by bogie5464 on 2011-03-20
I have been working closely to the Katana boot kit here recently, and this is bugging me. I am trying to use a new program to Katana called Forge. I have it on my flash drive, and I open the properties to make it executable, and when I click something it automatically changes back. I have tried the basic stuff, sudo nautilus. Yet it persists to give me this problem. Any idea why? Any workarounds? It did this in 10.04 and 10.10.

---

### Post by plucky on 2011-03-20
> **bogie5464 said:**
> I have been working closely to the Katana boot kit here recently, and this is bugging me. I am trying to use a new program to Katana called Forge. I have it on my flash drive, and I open the properties to make it executable, and when I click something it automatically changes back. I have tried the basic stuff, sudo nautilus. Yet it persists to give me this problem. Any idea why? Any workarounds? It did this in 10.04 and 10.10.

Flash drives are normally Fat32 format and linux file permissions won't work the same as on an ext2/3/4 partitions.You should either copy the file off the flash drive and then change the execute bit or format the flash drive to ext2/3/4 and then you can use it as normal on linux.

Personally I would keep the flash drive as Fat32 and copy the file to your hard drive.

Good Luck

---

