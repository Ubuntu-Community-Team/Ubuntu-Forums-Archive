---
title: "Midnight Commander"
date: 2004-10-19
forum: General Help
---

### Post by jdelo on 2004-10-19
How do you find midnight commander for install? Does it have noticable advantages over Nautilus?

Thanks,
Jeff

---

### Post by Rancoras on 2004-10-19
It's in universe.  Have a look at the FAQ forum to find out how to enable universe.

---

### Post by ulefr01 on 2004-10-19
Edit your /etc/apt/sources.list with your favorite text editor

sudo vi /etc/apt/sources.list

Add these 2 lines to the list.
Code:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted universe


Afterwards
sudo apt-get update

---

### Post by LongTooth on 2004-10-19
You can make the same changes using Synaptic. It will carrie over and when you use Apt-get via the CLI, universe will work.

---

### Post by misGnomer on 2004-10-20
Also check out [Gnome Commander](http://www.nongnu.org/gcmd/) which is a Gnome/GTK2 rendition of MC.

---

### Post by HungSquirrel on 2004-10-20
Hey, thanks for the link.  I installed that via Synaptic and I don't think I'll ever touch Nautilus again.   8)

---

### Post by rednax0 on 2008-06-14
> **misGnomer said:**
> Also check out [Gnome Commander](http://www.nongnu.org/gcmd/) which is a Gnome/GTK2 rendition of MC.

Okidoki, this works great. On Windows i have worked with [total commander]("http://www.ghisler.com") for 15 years (and before that NC on DOS), so this is easy.

I miss dragging a file to the delete button tough. :)

---

