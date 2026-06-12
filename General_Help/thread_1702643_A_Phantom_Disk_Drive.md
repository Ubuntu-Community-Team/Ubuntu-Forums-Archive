---
title: "A Phantom Disk Drive"
date: 2011-03-08
forum: General Help
---

### Post by JBA2337 on 2011-03-08
I am using Ubuntu 10.10. 

I have what seems to be a weird problem

For about a week I had another hard drive (with an NTFS partition) connected to my computer via a USB cable. Now I have disconnected this drive, but every time I boot up Ubuntu it is still searching for this drive. Whenever I boot up I get the following message. "The disk drive for /media/G is not ready, or not present. Continue to wait or press S to skip mounting or M to mount manually". Ubuntu for some reason wants to connect this drive, even though it is not physically connected to the computer.

I looked in the /media directory, and I was surprised to see /media/G there. In addition there is an actual copy of all the data on drive G (32.9GB) in /media/G. Though I didn't ask it to, Ubuntu copied everything from drive G to /media!

How do I get rid of the annoying message above?

Should I just delete /media/G?

Thanks.

JBA2337

---

### Post by Grenage on 2011-03-08
It might be listed in fstab; I don't know why it would be, unless present at time of install.

From a terminal:

```
sudo cp /etc/fstab ~/backupfstab
gksu gedit /etc/fstab
```

Remove or comment out the line that refers to the old drive.  If all is well, you can delete the backup in your home folder, the one we made with the first command.

Regarding the data in /media, I've never seen Ubuntu copy data there before.  I assume you're positive that the drive isn't plugged in, or that you didn't run some command to copy the data?

---

### Post by JBA2337 on 2011-03-08
> **Grenage said:**
> It might be listed in fstab; I don't know why it would be, unless present at time of install.

From a terminal:

```
sudo cp /etc/fstab ~/backupfstab
gksu gedit /etc/fstab
```

Remove or comment out the line that refers to the old drive.  If all is well, you can delete the backup in your home folder, the one we made with the first command.

Regarding the data in /media, I've never seen Ubuntu copy data there before.  I assume you're positive that the drive isn't plugged in, or that you didn't run some command to copy the data?
__________________________________________________________________________

To Grenage:

Thank you very much, I followed your suggestions, and the problem went away. 

Drive G was listed in fstab, so after making a backup of fstab, I deleted the lines that were trying to mount drive G. I also deleted all of the information from drive G that was in /media. I don't have any idea how drive G got copied into /media. 

Anyway, your suggestions worked and my problem is now solved.

THANK YOU!!!

JBA2337                      :D

---

### Post by Grenage on 2011-03-08
Glad to hear it. :)

---

