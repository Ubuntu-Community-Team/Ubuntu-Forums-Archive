---
title: "USB Mount problems after upgrade"
date: 2010-05-08
forum: General Help
---

### Post by Rob0147 on 2010-05-08
Dear Forum

I have upgraded from ubuntu 9.10 to 10.4 and all has gone smoothly apart from one thing.

I went to go and launch my virtual box ose program and it came up with the following error:

 error VERR_FILE_NOT_FOUND opening image file.


The image file itself lives on an external usb hdd drive. upon further investigation I found that the usb drive is not mounting as it used to do. when i looked in the /media folder I found an x on the old mount folder and the usb drive has mounted under a new folder name.

I can only put this down to the upgrade and I would love to configure it so that the usb drive is mounting under the original folder name. I have had a good look on the forum and I can't find anything that pertains to the problem I am having so hopefully someone on here can point me in the right direction.  I am certain that once this mounting issue has been resolved then  virtual box will be working again.


thanks in advance

Rob

---

### Post by chappajar on 2010-05-09
You can edit /etc/fstab to mount it where you want.  There are millions of threads here on /etc/fstab, just search.

---

### Post by Rob0147 on 2010-05-09
I actually managed to solve the problem another way.

I did Alt+F2. 
In the box that came up I typed gksudo nautilus.
I was then able to browse to the /media folder where I was able to delete the folder with the x on it.
I then plugged in the usb drive and it mounted under the original name it did before and I was able to use virtualbox ose.

thanks

Rob

---

