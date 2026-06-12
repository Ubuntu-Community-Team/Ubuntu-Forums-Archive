---
title: "Undelete RW2 Files Deleted Via &quot;rm&quot;"
date: 2010-06-20
forum: General Help
---

### Post by GreaterCore on 2010-06-20
Hi guys, I need help with undeleting a bunch of files for a friend. So far I have ran "extundelete" and it has retrieved a bunch of JPG files successfully, but it did not return any RW2 files (it is a raw format from Panasonic digital cameras). Any clues on how I can proceed to get them undeleted?

Just in case I messed up, I made an image of the said harddisk into a file. Unfortunately since all I had was a Fat32 drive, I had to split all the files to under 4GB.

So I ran "dd -if /dev/sdc4 | split -b 4GB" and gotten a bunch of files. So now to add insult to injury, I will need to somehow piece those files together again before I can rerun a search for it. The file system I am examining is EXT4.

To keep things simple, my question boils down to two.
[LIST=1]
[*]Are there any recovery software that searches for RW2 files on EXT4 filesystems?
[*]Are there any software that recovers by searching an image split across many files?
[/LIST]

---

