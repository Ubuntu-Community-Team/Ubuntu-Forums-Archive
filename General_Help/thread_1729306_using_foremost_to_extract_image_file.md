---
title: "using foremost to extract image file"
date: 2011-04-14
forum: General Help
---

### Post by blompy on 2011-04-14
I've got an image file on my Ubuntu desktop from using ddrescue.  

When I use the *foremost* tool to extract the files onto an external drive, I keep getting an error:

**sudo foremost -i ~/Desktop/backup.img -o /mnt/sda2**
ERROR: /mnt/sda2 is not empty
     Please specify another directory or run with -T.


I am able to extract the files from the image file to the Ubuntu desktop, but there is not enough room on my Ubuntu partition to hold all the files.

Any help appreciated

---

### Post by ~Plue on 2011-04-14
make sure /mnt/sda2 is empty. else, you could output to an empty subdirectory

sudo foremost -i ~/Desktop/backup.img -o /mnt/sda2/foremost-output/

//note: you wont need to use sudo if you have read/write permissions to the image and the target directory

---

### Post by blompy on 2011-04-14
thanks, got it working  


:)

---

