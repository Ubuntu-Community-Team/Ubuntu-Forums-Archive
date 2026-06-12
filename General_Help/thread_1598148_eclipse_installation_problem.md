---
title: "eclipse installation problem"
date: 2010-10-16
forum: General Help
---

### Post by kanishkdudeja on 2010-10-16
hey guyz..

jus downloaded eclipse for linux 32-bit from here..

[http://eclipse.org/downloads/](http://eclipse.org/downloads/)

the 205 mb file..

but when i open it, or try to extract it..

it shows..

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now

please help

---

### Post by kanishkdudeja on 2010-10-16
please help

---

### Post by lykeion on 2010-10-16
Sounds like the downloading is corrupted. You could try to re-download it and see if it helps.
Otherwise open a terminal (Applications > Accessories > Terminal)
Go to the directory where you've downloaded the file (in code below I assume it's in Desktop directory):
```
cd Desktop
```
Then determine if the downloaded file is indeed a gzip archive (assuming you downloaded Eclipse IDE for Java EE Developers, 205 MB, 32-bit):
```
file eclipse-jee-helios-SR1-linux-gtk.tar.gz
```
If it says the file is "gzip compressed data" then you should be able to extract it without errors.
You can also check the MD5 of the file to see if it's corrupted:
```
md5sum eclipse-jee-helios-SR1-linux-gtk.tar.gz
```
Compare this with the MD5 from the Eclipse website
[http://download.eclipse.org/technology/epp/downloads/release/helios/SR1/eclipse-jee-helios-SR1-linux-gtk.tar.gz.md5](http://download.eclipse.org/technology/epp/downloads/release/helios/SR1/eclipse-jee-helios-SR1-linux-gtk.tar.gz.md5)

If output match the file should be OK.

---

### Post by luvshines on 2010-10-16
> **kanishkdudeja said:**
> hey guyz..

jus downloaded eclipse for linux 32-bit from here..

[http://eclipse.org/downloads/](http://eclipse.org/downloads/)

the 205 mb file..

but when i open it, or try to extract it..

it shows..

gzip: stdin: not in gzip format
tar: Child returned status 1
tar: Error is not recoverable: exiting now

please help

You could have installed eclipse from Synaptic manager.

---

### Post by kanishkdudeja on 2010-10-16
when i type file eclipse-jee-helios-SR1-linux-gtk.tar.gz in the terminal..

it shows:

eclipse-jee-helios-SR1-linux-gtk.tar.gz: data

and ive checked the md5 it does not match..:(

---

### Post by luvshines on 2010-10-16
> **kanishkdudeja said:**
> when i type file eclipse-jee-helios-SR1-linux-gtk.tar.gz in the terminal..

it shows:

eclipse-jee-helios-SR1-linux-gtk.tar.gz: data

and ive checked the md5 it does not match..:(

That points to a corrupted file. You'll have to redownload it, I guess :(

---

### Post by James78 on 2010-10-16
> **luvshines said:**
> You could have installed eclipse from Synaptic manager.
Preferable, except for the fact that the new release, Helios, isn't in the repositories.

---

### Post by kanishkdudeja on 2010-10-16
ok thanks guyz..but i wanted to ask..i downloaded it from the bittorent specified on eclipse.org/downloads..n it downloaded fully..so how can ue be corrupted ?

---

### Post by kanishkdudeja on 2010-10-16
ok thanks guyz..but i wanted to ask..i downloaded it from the bittorent specified on eclipse.org/downloads..n it downloaded fully..so how can it be corrupted ?

---

### Post by josepgl on 2010-10-16
> **kanishkdudeja said:**
> ok thanks guyz..but i wanted to ask..i downloaded it from the bittorent specified on eclipse.org/downloads..n it downloaded fully..so how can it be corrupted ?

If you downloaded it with Transmission you can verify the local data and it will look for corrupted blocks and will download them again, it happened to me a few times. Other bittorrent software should be able to check for corrupted blocks too.

---

### Post by James78 on 2010-10-16
> **josepgl said:**
> If you downloaded it with Transmission you can verify the local data and it will look for corrupted blocks and will download them again, it happened to me a few times. Other bittorrent software should be able to check for corrupted blocks too.
That's one of the best features that torrent programs have.

---

### Post by kanishkdudeja on 2010-10-17
thanks but ive deleted the file now..:(

---

### Post by lswinkel on 2012-06-13
I actually have the same problem as above, downloaded the most recent Indigo eclipse yet seem to get different md5sums each time I download it..

The problem is even worse, I tried multiple servers(mirrors) to no avail and installing from the repositories also yields an error ( something wrong with my normal & functional internet connection it claims ).

Please see the attached screenshot, very strange situation this is..

I will try to use bittorrent download with optional corruct block fix new and update this thread later.

---

### Post by lswinkel on 2012-06-13
Ok, I have solved this problem on my own system.

1. I attempted to download using bittorrent
2. It used KTorrent which I apparently had installed ( almost never user bittorrent so forgot )
3. KTorrent opened ( via KDE's file manager Dolphin and associations ) Ark instead of default zipped-file tool for Gnome/Unity Archive Manager
4. Opened and extracted without problems

Now, it have a working eclipse, the problem was somehow in Unity/Gnome/Archive Manager.

---

