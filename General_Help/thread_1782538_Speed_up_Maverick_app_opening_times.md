---
title: "Speed up Maverick app opening times"
date: 2011-06-14
forum: General Help
---

### Post by terrykiwi83 on 2011-06-14
Just looking for some tips here, I run Mint 10 (Ubuntu 10.10 Maverick x64) and opening applications and documents is pretty slow. Does anyone have any tips to improve performance? am talking 10-15 secs to just open a document which should be pretty instant. 

My specs are: Intel i7 950, 8GB DDR3 RAM, 64GB SSD Drive, 2 x 1TB SATA2 Drives, nViDia GTX470.

Any help appreciated :)

---

### Post by terrykiwi83 on 2011-06-14
Think I may have just figured it out, I have setup Prelinking and it has made a HUGE difference - programs run instantly and I haven't had any problems with it - plus easy setup.

In Maverick ''prelink' is available in the software center just install it from there then make these edits to enable.

```

gksu gedit /etc/default/prelink

```

Change the line that reads PRELINKING=unknown to PRELINKING=yes then save file and quit gedit.

Finally to run a prelinking scan in terminal type

```

sudo prelink -a

```

This will prelink practically all binary files on your computer and may take some time to complete. You may also see some error output, but you don't need to pay attention or worry about this.

Now enjoy super fast application launching times.

---

### Post by Jouke74 on 2011-06-15
With this computer and using the SSD as disk for documents and programs you should have a very responsive system anyway? There might be something more going on with your disk controller or partition alignment on the SSD. Futhermore, of you are using the TB disks to load everything up, then you might consider using the SSD :D

Prelinking works by linking the needed libraries to the executables. In the latest versions of Ubuntu this should not make a huge amount of difference. Be careful with updates of the libraries and enjoy your fast system.

---

