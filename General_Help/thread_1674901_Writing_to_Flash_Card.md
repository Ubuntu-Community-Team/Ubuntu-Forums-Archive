---
title: "Writing to Flash Card?"
date: 2011-01-24
forum: General Help
---

### Post by pmptg on 2011-01-24
I have a flash card that has been corrupted and have obtained a working .img file. I was told that I could not just drag and drop the .img to the card and that it needs to be written bit by bit to the new card. I am unfamiliar with the Linux terminal and would like to know what command or a how to get the .img file written to it. The .img file is now residing on the desktop.

Thank You,

Paul

---

### Post by corncob on 2011-01-24
I only ran into an .img file once years ago and someone here helped me by pointing out an application that made it a snap to extract.  Unfortunately, I can't find the app or the post but did come up with this:
```
http://ubuntuforums.org/showthread.php?t=180668
```

---

### Post by pmptg on 2011-01-24
Thanks for the thread, how do I know what drive is my compact disk reader?

---

### Post by Nytram on 2011-01-24
Insert your flash card and run this command:

> sudo fdisk -l

You can find the device by its size. Just be sure you get it right or the dd command will happily write over your hard drive/system.

---

