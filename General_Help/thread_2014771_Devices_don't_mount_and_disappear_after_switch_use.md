---
title: "Devices don't mount and disappear after switch user"
date: 2012-07-02
forum: General Help
---

### Post by francisco2007 on 2012-07-02
Hi All, 

I have two separate issues (maybe they are linked, I don't know...).

I'm using Ubuntu 12.04, fresh install.

The first -
When I log in to my account (admin), I have to open Nautilus, and click on each hard drive under the media list, to make it mounted (right term?) and show on the left panel. Some of the drives are NTFS. How do I make them mount without the hassle?

The second - 
When my wife log in to her account (switch user), she doesn't see any of NTFS drives in Nautilus. I tried setting her account to admin, but it didn't solve it. What should I do?

Any help will be appreciated.

---

### Post by msammels on 2012-07-03
You want the drives to auto-mount when a user logs on? You'll need to use the terminal for this. Open up a terminal and type the following:

```
sudo blkid
```

Take note (copy/paste somewhere) any line that has 'TYPE="ntfs"' at the end.

Then, back in the terminal:

```
sudo gedit /etc/fstab
```

Then add this line to the bottom of each file, and save it:

```
UUID=xxxxxxxxxxx /mnt/Windows ntfs users,defaults 0 0
```

"xxxxxxxxxxx" is the UUID you took note of in the previous step. You will need more than one line, depending on how many drives you wish to auto load. Also - make sure the mount point is different ("/mnt/Windows" won't work on them all!)

---

