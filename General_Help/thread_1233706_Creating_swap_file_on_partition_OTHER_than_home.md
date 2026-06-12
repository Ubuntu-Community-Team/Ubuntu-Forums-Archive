---
title: "Creating swap file on partition OTHER than /home"
date: 2009-08-07
forum: General Help
---

### Post by theromanone on 2009-08-07
I have 2 partitions, one that the ubuntu jaunty 64-bit is installed and the other with all my files. I would like to create a swap file to use while hibernating in the 'files partition, since when suspending I just get a bunch of repetitive "error" files, is this possible?

I realize this can create a swap file:
[http://www.go2linux.org/Swap-memory-increase-with-swap-file](http://www.go2linux.org/Swap-memory-increase-with-swap-file)

- but that creates one in the ubuntu root partition (/).. something that I don't have HD space for.

---

### Post by pastalavista on 2009-08-07
You'll need to use gparted (Partition Editor) to shrink the media partition. It comes with the live CD in the System-> Administration menu but you can install it
easy enough```
sudo apt-get install gparted
``` Run gparted, right-click the drive you want to resize and 'unmount' it. Shrink it enough to leave about as much empty space as you have RAM or up to 50% more if you don't have much RAM. Then format the empty space as 'swap'.

---

### Post by mikewhatever on 2009-08-07
It looks like all you need to do is substitute a different path to /swapfile. I have no idea if it is going to work, but, let's say the storage partition is mounted under /media, then a possible path would be /media/storage/swapfile. It's important that you verify what the mount point is, as well as the mount location.

---

### Post by pebo on 2009-08-07
As far as I can tell you can create a swap file wherever you want in the filesystem - see [this]("https://help.ubuntu.com/community/SwapFaq#Example%20of%20making%20a%20swap%20file") link. Just make the file on your files partition, instead of "/mnt/512Mb.swap" in the example.

---

