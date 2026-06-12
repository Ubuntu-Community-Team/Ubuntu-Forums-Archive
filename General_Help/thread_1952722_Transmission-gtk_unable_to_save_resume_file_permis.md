---
title: "Transmission-gtk: unable to save resume file: permission denied"
date: 2012-04-04
forum: General Help
---

### Post by asuastrophysics on 2012-04-04
Hey guys,

I've been having this weird problem with bittorrent for as long as I can remember. About midway through the download, the torrent will turn red and read:
"unable to save resume file: permission denied"

I won't get this message as long as I run bittorrent-gtk as root, but I shouldn't have to do that. (Furthermore, running as root will make all of the downloads the exclusive property of root).

I tried running this:
```
sudo apt-get --purge transmission-gtk
```
and then reinstalling the program, but I get the same result. Has anyone else had this error?

---

### Post by dniMretsaM on 2012-04-04
I would guess wherever you are trying to save the file (or possibly the file itself) is owned by root.

---

### Post by asuastrophysics on 2012-04-04
> **dniMretsaM said:**
> I would guess wherever you are trying to save the file (or possibly the file itself) is owned by root.

Thanks for your response. 
That's what I thought also, but the download location is /home/myuser/Downloads, which is a directory owned by me. 

I even did a search in the computer for "transmission-gtk". It came up with around 8 results. I ran chown -R myuser:myuser on all of these files, effectively giving me ownership of transmission, and I still get the error message. This confuses me a wee bit :confused:

---

### Post by dniMretsaM on 2012-04-04
Are you sure the permissions on the file didn't get changed accidentally? Also, be sure you own the .torrent that you are downloading from and the partial file (might be .part, I'm not sure).

---

### Post by asuastrophysics on 2012-04-04
> **dniMretsaM said:**
> Are you sure the permissions on the file didn't get changed accidentally? Also, be sure you own the .torrent that you are downloading from and the partial file (might be .part, I'm not sure).

Strangely, you are 100% correct: :p
```
jakob@jake-desktop:~/Downloads$ ls -l
total 776940
drwxr-xr-x 2 root  root       4096 2012-03-10 21:17 Torrent 1
drwxr-xr-x 2 root  root       4096 2012-04-04 21:23 Torrent 2

```

That's very strange though. So by default, all torrent files have ownership of root, regardless of what permissions were used to run firefox, the program that downloaded the file. Is there a way to change this?

---

### Post by dniMretsaM on 2012-04-05
> **asuastrophysics said:**
> Strangely, you are 100% correct: :p
```
jakob@jake-desktop:~/Downloads$ ls -l
total 776940
drwxr-xr-x 2 root  root       4096 2012-03-10 21:17 Clerks [The First Cut].1994.BRRip.XviD.AC3[5.1]-VLiS
drwxr-xr-x 2 root  root       4096 2012-04-04 21:23 Extremely Loud And Incredibly Close {2011} DVDRIP. Jaybob

```That's very strange though. So by default, all torrent files have ownership of root, regardless of what permissions were used to run firefox, the program that downloaded the file. Is there a way to change this?

First off, I'm going to assume you already own the two movies you are downloading and that it is legal in your jurisdiction to download copies of works that you own a legitimate copy of.

Anyway, one possible reason for the change is that the first time you opened Transmission to dl the files you inadvertently opened it as root. Other than that, I really don't know. I looked around in the preferences but didn't see anything that would affect that. Sorry I can't be of any more help.

---

### Post by andrew.46 on 2012-04-06
> **asuastrophysics said:**
>  Is there a way to change this?

I assume you manually changed the permissions of the 2 downloaded torrents? This would at least get the torrents resumed...

---

### Post by colin.p on 2012-04-06
When I used to use Transmission, I would get that error, however, the file would generally download after awhile. I no longer use Transmission (use Deluge) and I also no longer get that error. Everything downloads as it should.

---

