---
title: "edit .deb package contents"
date: 2011-02-13
forum: General Help
---

### Post by Bucic on 2011-02-13
I'm dealing with a driver installer that tries to download something from a dead link. The standard archive manager opened the problematic deb package

```
firmware-b43-installer_4.150.10.5-4_all.deb
```

I extracted it and hunted the file that contains the dead link

```

DEBIAN\postinst
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```

I'd like to change the link to a working URL change to
[http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) but the standard archive manager won't allow for direct in-archive (deb) editing of any files. I've edited extracted file but I can't avorwrite the file that's inside deb now (overwirite old postinst with new postinst). 

I also tried re-creating a deb package from all the contents:
- extracted the old deb and modified the postinst in it
- compressed to ar
- changed the file extension to deb
- also tried the same as above but with tar.gz
- Ubuntu Software Center says "Could not be opened" in both cases

Can someone help me ASAP, please?

---

### Post by gmargo on 2011-02-13
Easy to do with the **dpkg-deb** tool.

Extracting:
```

mkdir /tmp/b43
cd /tmp/b43
dpkg-deb -x /path/to/firmware-b43-installer_4.150.10.5-4_all.deb .
dpkg-deb -e /path/to/firmware-b43-installer_4.150.10.5-4_all.deb

```Now edit the **DEBIAN/postinst** file to modify the wget path.

Rebuilding:
```

dpkg-deb -b . ../firmware-b43-installer_4.150.10.5-4new_all.deb

```Now save the new .deb file to a better directory than /tmp, then install it using:
```

dpkg -i firmware-b43-installer_4.150.10.5-4new_all.deb

```

---

### Post by Bucic on 2011-02-14
Thanks!

Although I cracked it myself while waiting for replies. After I prepared a folder with deb contents including the modified file I simply followed steps 13 to 16 described here [http://ubuntuforums.org/showthread.php?t=962835](http://ubuntuforums.org/showthread.php?t=962835)

  By 
```
dpkg-deb -b >>>. ..<<<

```you mean 'path to' again?



One more thing. 
Is it possible to make it 100% offline package i.e. including the file to be downloaded in the package and replacing the wget fragment with... you know what I mean.


______________
BTW, what kind of moron prepares an OFFICIAL (and **UBUNTU**) network driver package/installer that requires network access in the first place?! I really have to find out the name of this Einstein [IMG]http://forums.eagle.ru/images/smilies/doh.gif[/IMG]

---

### Post by gmargo on 2011-02-14
> **Bucic said:**
> 
```
dpkg-deb -b >>>. ..<<<

```you mean 'path to' again?

Not sure what you mean.  The first dot is the first argument to the -b option (source directory).   The two dots is part of the .deb pathname which is the second argument to the -b option (destination archive file). "-b . /path/to/file.deb" means build from the current directory into the specified archive file. I used a relative pathname in this case.

> 
Is it possible to make it 100% offline package i.e. including the file to be downloaded in the package and replacing the wget fragment with... you know what I mean.
Of course, but that probably violates license terms on the Broadcom binary.

---

### Post by Bucic on 2011-02-14
> **gmargo said:**
> Not sure what you mean.  The first dot is the first argument to the -b option (source directory).   The two dots is part of the .deb pathname which is the second argument to the -b option (destination archive file). "-b . /path/to/file.deb" means build from the current directory into the specified archive file. I used a relative pathname in this case.
Ah, I see. So it's an actual command argument, not some <enterhereyourusername> text.

> **gmargo said:**
> 
Of course, but that probably violates license terms on the Broadcom binary.
Could we do that? I'm going abroad and the last thing I want is to be forced to ask someone for a cable to get my wireless working...

---

### Post by gmargo on 2011-02-14
> **Bucic said:**
> Could we do that? 
Not we.  But now you know how to build a .deb archive, so a clever person could figure it out. :)

---

### Post by Bucic on 2011-02-14
> **gmargo said:**
> Not we.  But now you know how to build a .deb archive, so a clever person could figure it out. :)
Not really as the modification requires knowledge of terminal commands that instead of downloading something from an URL will fetch it from the package itself ot at least from HDD. In such a scenario I'm clueless.

---

