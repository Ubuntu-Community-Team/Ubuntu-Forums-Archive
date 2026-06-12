---
title: "NIkon Electronic Format thumbnails (.NEF)"
date: 2012-10-13
forum: General Help
---

### Post by checoimg on 2012-10-13
Hi and thank you for your time.

I used to have thumbnails for .NEF files inside Ubuntu studio but they seemed to retire this function from the software so I came back to the Ubuntu Unity environment and I want to have NEF thumbnails right inside nautilus, is there a way to install this ?

---

### Post by conradin on 2012-10-14
[https://bbs.archlinux.org/viewtopic.php?id=118685](https://bbs.archlinux.org/viewtopic.php?id=118685)
maybe some thing along those lines, I dont use unity though so Im only guessing. 
Are you referring to exifprobe software?
There is NEF decoding sofware in the repos still, [http://www.cheeseplant.org/~daniel/pages/denef.html](http://www.cheeseplant.org/~daniel/pages/denef.html)

---

### Post by checoimg on 2012-10-14
Worked all fine! thank you for your help!

---

### Post by checoimg on 2012-10-23
Install gnome-raw-thumbnailer 

as root create, then edit the file

 /usr/share/thumbnailers/nef-thumbnailer.thumbnailer

to contain the following

[Thumbnailer Entry]
Exec=/usr/bin/gnome-raw-thumbnailer -s %s %i %o
MimeType=image/x-nikon-nef;

---

