---
title: "Damaged HDD?"
date: 2010-05-12
forum: General Help
---

### Post by LutraMan on 2010-05-12
I've tried to create a backup image using achronis but I've encountered some problems.
1) It showed that my primary HD is somehow damaged.
2) It was unwilling to accept my secondary HD as the destination drive.

some details:
- both of my HDD's are ext4 file systems.
- I've recently moved a very large capacity of media file (about 160GB) from my primary HD to my secondary (so that the backup image would fit)

I've already tried to use 'fsck' command, but I can't, because I can't find a way to unmount my primary partition.

I'm using Karmic.

any help would be greatly appreciated.

---

### Post by obaid on 2010-05-12
[www.clonezilla.org]("http://www.clonezilla.org")

---

### Post by bredman on 2010-05-12
To fsck your primary drive, boot from a live CD.

---

