---
title: "mount EXT4 in windows"
date: 2011-11-24
forum: General Help
---

### Post by paladin_knight on 2011-11-24
Hi, I would like to know if i can mount EXT4 file system in windows. I know there is Ext2ifs but I think it only mounts Ext2/3. Do you have any recommendation? Thanks.:P

---

### Post by JeremyT on 2011-11-24
It sounds like [Ext2Fsd]("http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/") will work with Ext4. Though, I can't promise anything as I haven't tried it.

---

### Post by paladin_knight on 2011-11-24
> **JeremyT said:**
> It sounds like [Ext2Fsd]("http://sourceforge.net/projects/ext2fsd/files/Ext2fsd/") will work with Ext4. Though, I can't promise anything as I haven't tried it.

I think it only works for Ext2 file system.

---

### Post by satanselbow on 2011-11-24
There is "experimental" support for ext4 as per [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

Last time I used this however I found it to be very unstable and mangled files left right and centre :(

If you need to share a drive with Win you would get more mileage using NTFS.

---

### Post by JeremyT on 2011-11-24
It looks like ext4 read support was added in 0.48 and write in the latest, 0.51.

---

### Post by Jagoly on 2011-11-24
Nope, I've used it, it works great with ext4. Although I don't know how good it's write support is, I chose to not enable that when I used it. I didn't trust windows with my important stuff. I only needed read support, as write support seems redundant when ubuntu can just read off of the windows drive anyway. But it may work anyway.

---

### Post by mastablasta on 2011-11-24
free (for home use) total commander has a plugin in for ext: [http://www.totalcmd.net/plugring/ext4.html](http://www.totalcmd.net/plugring/ext4.html)

---

### Post by paladin_knight on 2011-12-05
> **Jagoly said:**
> Nope, I've used it, it works great with ext4. Although I don't know how good it's write support is, I chose to not enable that when I used it. I didn't trust windows with my important stuff. I only needed read support, as write support seems redundant when ubuntu can just read off of the windows drive anyway. But it may work anyway.

I have tried the Ext2fsd. I can assign a volume drive on my linux partition. However, I cannot open it as I would need to format the drive. 

I used another alternative which is Ext2Read. It works flawlessly. But, you need to run as Administrator. :D

---

### Post by liferules on 2011-12-05
Ext2fsd works fine for me....

---

### Post by Jagoly on 2011-12-06
> **liferules said:**
> Ext2fsd works fine for me....

same for me, it took a bit of configuring to set up from memory though.

---

