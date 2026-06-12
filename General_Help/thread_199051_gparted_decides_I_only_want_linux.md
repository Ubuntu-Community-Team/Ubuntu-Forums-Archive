---
title: "gparted decides I only want linux"
date: 2006-06-18
forum: General Help
---

### Post by Fubu-ntu(for-us-by-us) on 2006-06-18
First off I want to say i'm very impressed with ubuntu and the community. I had messed around with linux before but it was the professionalism of this project that got me to try it again. However, it is hard to be that generous to ubuntu given my current setup, and hopefully someone can help.

I had kubuntu installed on a small 3gb partition and decided that I liked it and wanted to create some more space for it. So I boot up the live cd, set it to shrink my 50gb windows (ntfs) down 4gb (giving a 46gb windows) in order to reinstall on a bigger partition. Gparted starts this, the bar moves a little, but never gets above 0 and gives me an empty (no message at all) error box. A bit annoyed, I restart to go to windows and forget about it but now i have a grub error 17, no boot. Getting back into the live cd linux, the windows partition is of an unknown type. I can't mount it even though it's of the same size and it doesn't look like it was changed (in start/stop locations) at all. My data is I there, I assume, how can I get to it? Can I restore things (ideally the whole partition but if I can save some documents I would like to know that too)? Am a doomed to a long, difficult reformating and reinstallation of both windows and linux?

thanks for any assistance.

---

### Post by Ramses de Norre on 2006-06-18
Maybe you haven't got the ntfs support installed, do ```
sudo aptitude install libntfs8 ntfsprogs ntfstools
```

---

### Post by Fubu-ntu(for-us-by-us) on 2006-06-18
I tried the code but it was already installed.

It did recognize it as ntfs prior to the failed attempt at resizing.

---

### Post by Rui Pais on 2006-06-18
hi, 
maybe its a bug on gparted. Try:
```
sudo ntfsresize --size 46G /dev/hda1
```
(replace hda1 by your partition position if it's not that one)

if that fails (it should show you the reason on command line)
try to defrag win xp first, maybe something is blocking the resize...

---

