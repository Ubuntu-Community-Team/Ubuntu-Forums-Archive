---
title: "Are there any disadvantages with this?"
date: 2009-08-27
forum: General Help
---

### Post by kio_http on 2009-08-27
If I install ubuntu on reiserfs will it be as good as ext4? Can someone provide a chart comparing the filesystems? Does ext4 use up more space or not?

---

### Post by scouser73 on 2009-08-27
I don't have a chat to compare reiserfs & ext4, but I never had any problems with reiserfs.  Any reason as to why you're not using ext3?

---

### Post by P4man on 2009-08-27
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=3](http://www.phoronix.com/scan.php?page=article&item=ubuntu_ext4&num=3)

Check the next pages too.

I dont have experience with reiser, but apparently its good with small files, and a nightmare when something goes wrong with the fs.

---

### Post by wojox on 2009-08-27
You can read this:

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Personally I favor ext3.

---

### Post by oboedad55 on 2009-08-27
> **wojox said:**
> You can read this:

[http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Personally I favor ext3.

I'm running reiserfs on my desktop with no problems. Had a power blip and the file system was not trashed. If I had it to do over again, maybe I will... I would use ext3 as there is no discernible speed difference. You can google for benchmarks.

---

