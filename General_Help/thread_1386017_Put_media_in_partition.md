---
title: "Put media in partition"
date: 2010-01-20
forum: General Help
---

### Post by EienTatsu on 2010-01-20
I have a bunch of shared media on my HD that I want everyone on my Computer to be able to access. I want to put that media in everyones music/video folders without having redundant data. Is there anyway I can put it on another partition and store the media there but access it from the media folders. 

Also is there any way to enable anonymous access via ftp to the media folder.

---

### Post by nothingspecial on 2010-01-20
Yes.

You can create links.

So say you have another partition with a music folder and a videos folder in it, just hold down Ctrl and shift and drag them into each users home.

This won`t actually copy the contents but they will be able to access the contents from there.

---

### Post by john newbuntu on 2010-01-20
You could store your media on a separate partition and then just mount it(read-write or read-only) when your filesystem mounts at startup.  This way, everyone gets to view the files.   Also, future upgrades do not affect your media mount point.  This is so much like how you view windows from linux on a dual boot system.

I believe you can add anonymous ftp or even secure copy like scp to copy files over.

---

### Post by EienTatsu on 2010-01-21
> **nothingspecial said:**
> Yes.

You can create links.

So say you have another partition with a music folder and a videos folder in it, just hold down Ctrl and shift and drag them into each users home.

This won`t actually copy the contents but they will be able to access the contents from there.Anonymous users cant access the directories from the links

---

