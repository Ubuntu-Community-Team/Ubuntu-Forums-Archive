---
title: "md5 checksum help"
date: 2009-11-25
forum: General Help
---

### Post by ManyBeers on 2009-11-25
Ubuntu 8.04. What is the command used to check an md5 sum on an .iso file?

---

### Post by Sam on 2009-11-25
```
md5sum file.iso
```

---

### Post by bodhi.zazen on 2009-11-25
md5sum /path/to/your.iso

[HowToMD5SUM - Community Ubuntu Documentation]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by ManyBeers on 2009-11-25
> **Sam said:**
> ```
md5sum file.iso
```

That's the code I used but I couldn't get it to work for several tries (probably typing errors) but finally it took and produced the sum.
Thanks to both of you for offering help.

---

### Post by bodhi.zazen on 2009-11-25
To reduce typing errofs use tab completion.

Start typing a file or location and hit the tab key

```
cd /ho<tab>
md5sum ~/fil<tab>
```

---

### Post by cdo on 2009-12-12
> **Sam said:**
> ```
md5sum file.iso
```

When i put the above command into the terminal it says no such file or directory . I just downloaded an iso and  it appears as :  ubuntu-9.10-alternate-i386.iso . I don't know if the "alternate" designation is the problem or not as i got it from a mirror site  here in Asia .

I used the transmission built in torrent and see the blue Transmission symbol in the file system but right clicking just opens the desktop version .  Can someone guide me further ?

---

