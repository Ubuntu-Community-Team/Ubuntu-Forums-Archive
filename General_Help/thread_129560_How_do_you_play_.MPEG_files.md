---
title: "How do you play .MPEG files?"
date: 2006-02-14
forum: General Help
---

### Post by Zach1188 on 2006-02-14
When ever I attempt to play a .MPEG file, I get: 
> 
Totem could not play '*FilePath/FileName*'.

There were no decoders found to handle the stream, you might want to install the corresponding plugins.


---

### Post by equal on 2006-02-14
You need to install the proper codecs. I think it's this command:

sudo apt-get install ffmpeg

---

### Post by Zach1188 on 2006-02-14
It installed successfully, but I still get the same error.

---

### Post by awakatanka on 2006-02-14
[QUOTE=Zach1188]It installed successfully, but I still get the same error.[/QUOTE]
Try installing w32codecs also this link is a good source for a howto [http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

---

### Post by Zach1188 on 2006-02-14
> 
zach@zCOMP:~$ sudo apt-get install w32codecs
Password:
Reading package lists... Done
Building dependency tree... Done
Package w32codecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package w32codecs has no installation candidate

...

---

### Post by Jucato on 2006-02-14
Actually, you have to download the w32codecs manually and install it through dpkg, unless you want to do this through Automatix or Easy Ubuntu. Here's the link for the instructions in playing MP3's, MPEG's and the works.

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by anirban.sam on 2006-02-14
[QUOTE=Zach1188]When ever I attempt to play a .MPEG file, I get:[/QUOTE]

Just try, sudo apt-get install vlc

then,

right click after selecting the file & open with & vlc,

for permanent association, use "other" from "open with" menu, select vlc from multimedia tag, check " remember application association for this kind of file"

next time juck double clicking will launch vlc and play the .mpeg files & many more formats.

---

