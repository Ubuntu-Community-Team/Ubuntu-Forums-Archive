---
title: "Extracting DMG files"
date: 2006-06-17
forum: General Help
---

### Post by ironfistchamp on 2006-06-17
Hey I was using a torrent and the end file was a .dmg. Am I right in thinking this is a Mac disk image file. I don't have a Mac to extract it nor do I have a Windows installation to use MagicISO. What can I do?

I found some resources that told me to mount it. I followed the intructions and I was told it was the wrong fs. I then found a perl script to extract it but got the error

./dmg2iso.pl: /usr/local/bin/perl^M: bad interpreter: No such file or directory


What does this mean and how can I fix it. Or does anyone know of another way?

Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2006-06-17
I got the script working. I used dos2unix and the script ran fine. Too bad the dmg was corrupted. Thats 50hrs of my life wasted. :-x

---

### Post by xurizaemon on 2006-07-17
I had a DMG (uncompressed) of .toast files, which are actually .iso files anyway. I discovered the .toast files were plain ISO by doing
```

file MyDiskImage.toast

```
and looking at the output.

The command which worked for me to mount the DMG was
```

sudo mount -o loop -t hfsplus EFT.dmg /media/EFT

```

I'm running a stock Dapper kernel and didn't have to manually load the hfs or hfsplus kernel modules, the two commands above were all I needed to access the contents of my DMG.

I created the DMG 'uncompressed' in Apple Disk Utility, because I didn't know what kind of compression it would use or whether the disk would be mountable in Ubuntu if it was enabled.

OSX10.4 PPC / Ubuntu Dapper x86

---

### Post by Gen2ly on 2006-12-04
Would you post the script, pretty please?

---

Hmm OK.  This is the script I think he was talking about:

[dmg2iso]("http://vu1tur.eu.org/tools/")

Also tried to work it out over here:

[dmg2iso error]("http://ubuntuforums.org/showthread.php?t=128833&highlight=Can%27t+locate+Compress%2FZlib.pm")

 Still wasn't able to have it work.  Seems some .dmg files aren't able to be opened.

---

### Post by babil on 2008-02-08
run magic-iso with wine ([http://www.magiciso.com/](http://www.magiciso.com/)) ... works perfect with wine-0.9.54 ... 100% tested

sometimes dmg files are bzipped ... do a "file Perian_1.1.dmg" to check if it's bzipped ... if yes, "bunzip2 Perian_1.1.dmg" ... after that change the output file to "something.dmg" ... then open it with magic-iso

cheers ...

---

### Post by ironfistchamp on 2008-02-08
Wow thats a bit of a necrobump :P

Thanks for the answer, if I am stuck in this situ again I will use MagicISO.

Thanks

Ironfistchamp

---

