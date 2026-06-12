---
title: "Convert ext4 to ext3"
date: 2010-05-11
forum: General Help
---

### Post by landymann on 2010-05-11
Basically there is a problem with the SSD on my eee PC , where by there are some bad sectors, which are unfortumnatly being used by the ext4 filesystem, to recover the install I have to go in via a live CD and use this command ```
sudo fsck /dev/sda1 -f
```It seems that ext3 doesn't use bad blocks from what I can gather reading round the net. The previous 9.10 install was fine but this will put rectangles in place of text and won't show images, this the only thing connecting them is possible google chrome, but I doubt this would affect the whole system. Do I need to manually transfer the files? and if so will it still be bootable? So I want to convert the file system back.

---

