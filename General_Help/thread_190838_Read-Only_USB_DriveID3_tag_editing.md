---
title: "Read-Only USB Drive/ID3 tag editing"
date: 2006-06-06
forum: General Help
---

### Post by decide on 2006-06-06
So i've been using Dapper for a few days, it's my 3rd Linux distro (tried SUSE and Red Hat and never got into them, always went back to Windows).  I've finally got a grasp on how things work, i'm really happy that i'm not looking to going back to Windows anytime soon.

However, I do have some USB external HDs that I used for mass storage in Windows.  One of them has my extremely large music collection on it, which I can listen to, mounts wonderfully, etc.  However, when it comes to editing ID3 tags, using both AmaroK and EasyTAG, I can't edit them because the files are read-only.  Is there any workaround for this or am I screwed as far as editing my current collection?

Thanks!

---

### Post by aysiu on 2006-06-06
Is this an NTFS drive?

---

### Post by decide on 2006-06-06
Yup, forgot to mention that.  Was using it with XP just days ago.

---

### Post by aysiu on 2006-06-06
NTFS is read-only from Linux. Sorry. Maybe reformat the drive?

---

### Post by decide on 2006-06-06
Thank heavens for having more than one computer in a house!  Storing the files I have around multiple drives, I should be able to do that :)

Thanks!

---

### Post by musicinmybrain on 2006-06-06
By the way, if you want to share the drive between Ubuntu and Windows, you have a couple of options. FAT32 is one. EXT3 is [another]("http://fs-driver.org/"). (I haven't tried the IFS driver with a USB drive, but there's a good chance it works. I know it works with internal drives.)

---

