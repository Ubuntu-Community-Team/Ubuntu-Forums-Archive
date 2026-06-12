---
title: "How to see fsck report or bad block statistics"
date: 2011-12-05
forum: General Help
---

### Post by narcisgarcia on 2011-12-05
I run "fsck -cy" on an Ext4 partition, and it finds and reallocates inodes.

I need to know how many space is marked as bad in that partition, and don't find a software tool to report this.

---

### Post by narcisgarcia on 2011-12-08
I've found the following command, but I don't know how to interpret the results:
```
sudo dumpe2fs -b /dev/sda1
```

---

### Post by BoneZZZ on 2011-12-11
Have you used:

sudo badblocks -v /dev/sdb1

???

Change /dev/sdb1 with your own values.

Baeza ;)

---

### Post by narcisgarcia on 2011-12-11
But *badblocks* checks again the complete media surface, and I want to know the space already marked as bad.

---

### Post by BoneZZZ on 2011-12-12
And fsck -L filename?

---

### Post by narcisgarcia on 2011-12-12
Which file?
What happens when "Set badblocks list"?

---

### Post by narcisgarcia on 2011-12-13
I've found now that I can know the block size of a volume with:
```
sudo dumpe2fs -h /dev/sda1 | grep -ie "Block size:"
```
And I can see the amount of blocks which are reserved as bad in the filesystem:
```
sudo dumpe2fs -b /dev/sda1 | wc -l
```
Then I can get the total bytes of marked blocks with the following formula:
```
echo $(($(sudo dumpe2fs -h /dev/sda1 | grep -ie "Block size:" | cut -f 2 -d ":") * $(sudo dumpe2fs -b /dev/sda1 | wc -l)))
```

---

### Post by BoneZZZ on 2011-12-14
How did you find out the "| wc -l" option? There is nothing in man.

---

### Post by narcisgarcia on 2011-12-14
```
man wc
```
It's to count the number of lines (inode numbers) returned by dumpe2fs.

---

