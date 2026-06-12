---
title: "What to do with my Partitions"
date: 2010-05-18
forum: General Help
---

### Post by Elliotal on 2010-05-18
Just a quickie..
i have 3 partitions on my hard drives.

150gb windows vista, 75gb ubuntu 10.04, 75gb free ext3.

Just wondering what people reccomend i do?

Should i set up a seperate home partition? if so what are the benefits of this?
or just add the free 75gb onto my ubuntu?

cheers

---

### Post by mike555 on 2010-05-18
You could use the extra partition as backup .. setup a backup program to backup your /home folder .........
or you could format it as fat32 and be able to use it as backup from Ubuntu or Windows ....

---

### Post by oldfred on 2010-05-18
I like a shared partition for data with windows but would use NTFS. I have all photos, firefox and thunderbird profiles in a shared so I have the same data in both. Although I now am in XP very little.

FAT now has limitations - 4GB max & no journaling. I was using a FAT for backups and every backup was 4GB, of course when I converted backups to ext3 they were twice as large and I never had a backup in FAT.

If you want to do clean installs vs upgrades in place a separate /home has large advantages. As you can easily reinstall and not overwrite the /home partition, just the root partition. But either way you should be backing up /home.

---

### Post by dabl on 2010-05-18
About partitioning:

[http://kubuntuforums.net/forums/index.php?topic=3090704.0](http://kubuntuforums.net/forums/index.php?topic=3090704.0)

About swap:

[http://kubuntuforums.net/forums/index.php?topic=3099574.0](http://kubuntuforums.net/forums/index.php?topic=3099574.0)

Good tool:

[http://partedmagic.com/](http://partedmagic.com/)

---

