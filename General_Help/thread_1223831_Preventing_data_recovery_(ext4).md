---
title: "Preventing data recovery (ext4)"
date: 2009-07-26
forum: General Help
---

### Post by Xzenome on 2009-07-26
I have to return a computer under warranty and so they can test it, I want to leave it almost exactly in its current state. The problem is, I have an ext4 partition with sensitive data on it and when I delete my home directory, I don't want it to be recoverable. The ext4 partition needs to remain on the hard drive in its current state. I know there are utilities for Windows that allow you to write over the unused space to make sure it can't be recovered, but how can that be done with ext4? I'm sure unused inodes are theoretically recoverable otherwise. In fact, I saw a tool for ext3 at least.

I don't want to take chances, but I also can't wipe the HD or use thermite on it.

---

### Post by zarqoon on 2009-07-26
I am not aware of a tool, that reliably deletes files without wiping an entire partition.
If you want to delete the entire partition you can use dd to overwrite a partition device with random data. If you do it this way the filesystem present wont matter since you write directly to the device.

check the man pages or wikipedia for dd for information on how it works
[http://en.wikipedia.org/wiki/Dd_(Unix)](http://en.wikipedia.org/wiki/Dd_(Unix))

Of course writing directly to the partition device will delete the entire partition. If you only want to delete specific files you could try filling it to the brim with useless data after you delete them.
dd should also be able to help you there. Be very careful using dd since it can really make a mess of things up if you write to the wrong file/device.
I am not certain that will absolutely delete everything however since there are a few percent of free space reserved to ensure system stability.

If this is really very important data it might be better to not give the repair center your hard disk at all. They should be able to find any hardware problems that are not related to the hard disk without it.

---

