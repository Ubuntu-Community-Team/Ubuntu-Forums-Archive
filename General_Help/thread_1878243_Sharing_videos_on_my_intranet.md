---
title: "Sharing videos on my intranet"
date: 2011-11-09
forum: General Help
---

### Post by rmcellig on 2011-11-09
At the moment, I have a Mac formatted (HFS+) external USB hard drive connected to my iMac that I have some videos on. I want to be able to watch these videos from any computer in my house. I have a mix of PC's with Windows XP and Windows 7, two laptops running Mint 11 and Ubuntu Studio.

What are my options?

---

### Post by mikewhatever on 2011-11-09
Samba is the way to go, or I should probably say 'your samba'. You can read more on what your samba is [->here<-]("https://help.ubuntu.com/community/Samba"), and there is no end of howtos on sharing content. Basically, you just right click your folder, select your 'Sharing Options' and share away.

[http://www.youtube.com/watch?v=89hjWOb8qmY](http://www.youtube.com/watch?v=89hjWOb8qmY)

---

### Post by rmcellig on 2011-11-09
I know about Samba but I think there might be a problem with the external USB drive being formatted as HFS+. Should I reformat it to something like FAT32 so that it is compatible on all platforms?

---

### Post by mikewhatever on 2011-11-09
Really don't know about HFS+. Regardless, I think NTFS would be a better choice then FAT32, because of the 4GB file size limit in FAT32. A video file can easily go beyond that size.

---

### Post by Lars Noodén on 2011-11-09
Linux can read/write HFS+ just fine, just not journaled.  So you may want to turn off journalling.  NTFS and FAT are very poor file systems and should be avoided when at all possible.  You'll need hfsplus, hfsutils, and hfsprogs.

---

### Post by CatKiller on 2011-11-09
DLNA is probably a good bet. I use MediaTomb on Linux as my media server but there's probably something available for your Mac too. There are DNLA clients for all platforms.

---

### Post by rmcellig on 2011-11-09
I did turn journalling off on the external USB drive but over a share, I can see the files on the Linux laptop. I just can't open them or even copy them over to my Linux HD. I keep getting an error coming up that that capability has not been implemented even though I have a wide open privileges on the USB drive so everyone can access it etc...

---

### Post by rmcellig on 2011-11-09
What is DNLA? I never heard of it.

---

### Post by rmcellig on 2011-11-09
> **Lars Noodén said:**
> Linux can read/write HFS+ just fine, just not journaled.  So you may want to turn off journalling.  NTFS and FAT are very poor file systems and should be avoided when at all possible.  You'll need hfsplus, hfsutils, and hfsprogs.

So I will need to install hfsplus, hfsutils, and hfsprogs on my Linux machines in order for this to work? I agree about NTFS and FAT32. I'm just looking for an alternative that will work for me.

---

### Post by CatKiller on 2011-11-09
> **rmcellig said:**
> What is DNLA? I never heard of it.[Digital Living Network Alliance]("http://en.m.wikipedia.org/wiki/Digital_Living_Network_Alliance")

---

