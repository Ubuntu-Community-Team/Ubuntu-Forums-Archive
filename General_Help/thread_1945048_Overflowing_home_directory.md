---
title: "Overflowing home directory"
date: 2012-03-22
forum: General Help
---

### Post by forste on 2012-03-22
Hi,

I am having the problem that my home directory is running out of space. Weirdly I can not find the source of the overflow:

```
> du -ch --max-depth=1 | sort -h 
56K	./.swt
68K	./.FBReader
128K	./.gnome2
176K	./.purple
192K	./.macromedia
416K	./.appdata
424K	./.icedtea
456K	./.gimp-2.6
596K	./.kde
664K	./.fontconfig
700K	./.ghc
864K	./.gstreamer-0.10
956K	./.ivy2
1.1M	./.libreoffice
2.2M	./.gconf
2.9M	./.Skype
4.1M	./.adobe
9.8M	./.local
14M	./.npm
17M	./.dropbox
23M	./.thumbnails
42M	./.dropbox-dist
71M	./.config
151M	./.mozilla
341M	./.cache
784M	./.thunderbird
1.2G	./.cabal
18G	.
18G	total
```

---

### Post by Mait on 2012-03-22
Is that whole output? Where are Music, Videos, Documents, Downloads folders?

---

### Post by forste on 2012-03-22
yeah, that's all. I deleted the rest since I am not using it. My data is actually everthing on another partition.
 
btw, by now I can't boot anymore (boot stucks at "Stopping ana(h)ronistic cron"). 
 
going alt+1 and startx tells me that something can't compile my keyboard map cause of missing space.
 
I did 
```
 
cd ~

```
and
du -h --max-depth=1
which gives me the same output as before :/ weird because I could reboot before and the space was freed again. however, now it's stuck like that

---

### Post by Habitual on 2012-03-22
```
df -h
```

output please.

/ may be the real issue if /home is not a separate partition.

---

### Post by letoasty on 2012-03-22
you can possibly fix this issue by clearing your ~/.local/share/Trash folder. Deleting data does not automatically remove it, and it is instead moved there. You can also open your Trash and empty it that way.

If you can't boot, try booting into Recovery Mode by holding shift on start-up (may be different depending on your variant) and delete the aforementioned Trash folder.

---

### Post by forste on 2012-03-23
thanks for help guys.

I finally found the cause:

In emacs I use a package for saving and restoring session. This package asks on startup if I want to restore the session. However, since I had *emacs --daemon *in my startup script it would not run interactively and instead filled up the file *[I]~/.xsession-errors*[/I]. Since I don't have my home on a separate partition that also filled up /.

The main problem is that I didn't know that
```
du -ch --max-depth=1 | sort -h
```
apparently only shows directories. Include the *[I]-a*[/I] options if you want to see files as well!

---

