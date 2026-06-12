---
title: "can't read most of commercial dvd movies"
date: 2005-02-24
forum: General Help
---

### Post by alta_ir on 2005-02-24
Hello,

i m new with linux...
I d try to read my dvd movies like shrek2 and i can t....
i ve a dvd drive pionneer (scsi) ==> sr0

i created a symlink
ln -s /dev/sr0 /dev/dvd

i installed libdvdcss2, and several players like gmplayer, wxvlc, ogle, gxine, etc...

but i m lost...
i can only watch dvd movies without css... (old movies and cartoons)

if you can help me.

ps: sorry for my bad english...

---

### Post by mike998 on 2005-02-24
You need to add the following to your /etc/apt/sources.list

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

Then at a command prompt, type

sudo apt-get update
sudo apt-get install libdvdcss2

That should now allow you to watch DVDs

---

