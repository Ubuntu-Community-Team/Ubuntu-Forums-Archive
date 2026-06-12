---
title: "Files seem corrupt"
date: 2011-04-10
forum: General Help
---

### Post by barnesy on 2011-04-10
Hey,

I recently copied about 1TB of videos from one drive to another.  Now it seems like my videos(a lot but not all) are choppy or just end up freezing(mkv files seem to be the ones freezing).

Is it possible that the transferring of a large amount of data could have damaged my videos?  

Any help would be greatly appreciated.

Thanks!!

---

### Post by carl4926 on 2011-04-10
Unlikely
If they were damaged, they probably wouldn't play.

It sounds more like a graphics driver issue

---

### Post by Enigmapond on 2011-04-10
> **carl4926 said:**
> Unlikely
If they were damaged, they probably wouldn't play.

It sounds more like a graphics driver issue

It may be however, I transferred videos from my NTFS drive to my ext4 drive and encountered a few problems in playing back. Prior to the transfer they all played well. So I have to say yes, it can happen.

---

### Post by barnesy on 2011-04-10
> **Enigmapond said:**
> It may be however, I transferred videos from my NTFS drive to my ext4 drive and encountered a few problems in playing back. Prior to the transfer they all played well. So I have to say yes, it can happen.


Well that really sucks.  I guess I should check everything before I format the drive.  It looks like I have a ton of work to do to get my videos back.

Thanks for the help.

---

### Post by lmarmisa on 2011-04-10
If you wish to check the integrity of the files you copied, I recommend to use the command [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM"):

```

man md5sum

cd /origin_dir
md5sum list_of_files
cd /destination_dir
md5sum list_of_files

```

---

