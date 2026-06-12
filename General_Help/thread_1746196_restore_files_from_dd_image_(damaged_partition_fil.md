---
title: "restore files from dd image (damaged partition file)"
date: 2011-05-01
forum: General Help
---

### Post by mivogt on 2011-05-01
hi there,

I did a bad mistake and had some mkfs running above my root harddisk.
I interrupted the mkfs by power-off the pc.

Now I miss all files stored on that disk.
I did a dd of the partition using the testdisk tool and got a .dd file with the size of the partion thar was hurt by mkfs.

If I check the content of the dd file using cat myImage.dd I can see some of my text- and html file content so maybe more of my data is somwhere inside this ...

If I try to mount the dd file to a loop device in any folder I can not see any files inside the target folder.

using:: mount -t auto -o loop,ro,umask=0222 ./myimage.dd /mnt/myfiles/

So this is where I need some help please.
How can I mount the dd file and get my files contained in it?

esp. I need back my /home dir with my kmail mailboxes....

thanks in advance


michael

---

