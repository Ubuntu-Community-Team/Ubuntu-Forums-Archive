---
title: "defrag all drives"
date: 2010-08-05
forum: General Help
---

### Post by DouglasAdams on 2010-08-05
i guess that, after a while, it's probably a good idea to defrag even a Linux system but there doesn't seem to be any options for doing this.
fyi, my 10.04 is on a partition of it's own, ditto /home, plus /boot, plus 5 other large partitions i use to store particular things all contained on two physical drives.
dunno if doing them all, one partition at a time or some other way is best so please explain.
thanks

---

### Post by kleskjr on 2010-08-05
no need to defragment ;)
If you don't believe me, read something about ext3/4
[http://www.whylinuxisbetter.net/items/defragment/index.php](http://www.whylinuxisbetter.net/items/defragment/index.php)

---

### Post by renkinjutsu on 2010-08-05
a good way to "Defragment" is to copy files around =]

Very inconvenient though. I'm sure you can write a script for that though. But generally, you do not need to defragment ext{3,4}.. Btrfs comes with a defragmentation tool though

---

### Post by darkstaar on 2010-08-05
> **kleskjr said:**
> no need to defragment ;)
If you don't believe me, read something about ext3/4
[http://www.whylinuxisbetter.net/items/defragment/index.php](http://www.whylinuxisbetter.net/items/defragment/index.php)

...and learn something important about women [grin].

---

### Post by DouglasAdams on 2010-08-05
ok, i believe you but i certainly don't believe that it was a woman who designed the method used to place files on the drive, as stated in the explanation you pointed me to. why would anyone lie about such an important issue? or is it just the usual case of let's big-up women regardless of it being true or not? if i'm wrong, please point me to the correct information.
wow! i thought, nay hoped, that a Linux forum would be a) free from such crap and b) have the guts to stick to the truth.

anyhow, sorry if i sounded ungrateful, i'm not, honest.
many thanks for clearing this up.

---

### Post by inameiname on 2010-08-05
You don't need to worry about defragging like with windows, but technically after a long while, there is a small, and I mean small, bit that gets fragmented. 

If you want a tool to defrag, which I use mainly for external NTFS and FAT32 drives, but can also use for EXT4, here you go:

Defrag.sh will defrag wherever you copy and paste the file into, so if you want it all, just copy and paste it into your home or root directory, or for all, your filesystem (/) directory.

FragCheck.pl will check whatever folder and all of it's subfolders for fragmentation and give you a percentage. (I had to zip this file as a perl script won't attach for some reason.)

Just open the terminal in whatever folder those two are, and './FragCheck.pl' and/or './Defrag.sh' them. You can also './FragCheck.pl /' or './FragCheck.pl ~' or './FragCheck.pl /root.

---

### Post by DouglasAdams on 2010-08-05
thanks everyone.
great help, as always.

---

