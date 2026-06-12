---
title: "A simple few things"
date: 2006-05-22
forum: General Help
---

### Post by zigoto on 2006-05-22
Hi, i want to do a few things on ubuntu 5.10, but i dont know i to do it.First i want to put the recycle bin on the desktop.
Another thing that i want to do is, always when i restart the computer i need to do the umount and mount of the partition that i have.
code that i need to do every time
```

sudo umount /media/hda5/
sudo mount /dev/hda5 /media/hda5/ -t ntfs -o nls=utf8,umask=0222

```
At last i want to change a icon of the documents that i create with openoffice.And can some one tell me how to put openoffice in portuguese!

Regards!

---

### Post by aysiu on 2006-05-22
For the automount go here:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Koori23 on 2006-05-22
Here's a quick way to get your trashcan back on the desktop.

I'm assuming you're using Ubuntu with Gnome here..

Click Applications->System Tools-> Configuration Editor

When that window comes up, find **Apps** then **Nautilus** and then **Desktop**.. On the right hand side you should see "trash_icon_visible", check the box. You may need to log off.. It's been a while for me.. But that's how you do it.

---

### Post by blackjack6.21.91 on 2006-05-22
i think a program called chron can automate your mounting/unmounting.  i'm not really a whizz with it, so maybe look it up and see if it can do anything for you??

and probably just download the portugese version of openoffice from the site and install it.  or maybe it's available with synaptic?

---

### Post by zigoto on 2006-05-23
hi, thanks, i have resolve all this things...

Regards

---

### Post by Ramses de Norre on 2006-05-23
[QUOTE=blackjack6.21.91]i think a program called chron can automate your mounting/unmounting.[/QUOTE]

The service is cron, but by just defining the right options in fstab you wont need this.

---

### Post by zigoto on 2006-05-23
hi, i have edit the fstab and it work fine!

---

