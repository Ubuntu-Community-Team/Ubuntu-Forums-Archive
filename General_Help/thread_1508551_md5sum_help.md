---
title: "md5sum help"
date: 2010-06-13
forum: General Help
---

### Post by COKEDUDE on 2010-06-13
Did I do this right? I have two different sets of numbers. I used these websites as references and can't tell if I did this right. 
[http://linux.byexamples.com/archives/198/md5-checksum-how-to/](http://linux.byexamples.com/archives/198/md5-checksum-how-to/)
[http://www.cyberciti.biz/tips/linux-unix-verify-dvd-cd-iso-images.html](http://www.cyberciti.biz/tips/linux-unix-verify-dvd-cd-iso-images.html)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

```
 ~/Desktop $ cd KN*
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso

^C
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ man md5sum
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ ls
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5.asc
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.sha1
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.sha1.asc
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
7559dbd329d8afeab1b54bf23d64eaef  KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
c29e505256e84ccb1943d92b6e6c5b24  KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ 

```

---

### Post by plucky on 2010-06-13
What are you expecting?

You have to compare the md5sum value given for the .iso file against the md5sum that is posted in a file at the download site.This then tells you the download doesn't have any file corruption.

The files you are running the md5sum on are different.The one called KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5 probably contains the md5sum for the .iso file.

Post output of that directory of ```
ls -lh
``` and what does ```
cat KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
``` show you.
It probably contains the correct value shown by ```
md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
c29e505256e84ccb1943d92b6e6c5b24  KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
```


Good Luck

---

### Post by lovinglinux on 2010-06-13
To make the process easier, use my Firefox extension [CheckIt](http://checkit-extension.blogspot.com). It allows you to easily select the md5sum posted on the web and compare with the downloaded file. Everything is done through Firefox context menu. The extension will warn you if they don't match.

---

### Post by gmargo on 2010-06-13
To double check against the .md5 file, use the -c option: 
```

md5sum -c KNOPPIX*.iso.md5

```Or against the .sha1 file:
```

sha1sum -c KNOPPIX*.iso.sha1

```

---

### Post by COKEDUDE on 2010-06-13
> **plucky said:**
> **What are you expecting?**

You have to compare the md5sum value given for the .iso file against the md5sum that is posted in a file at the download site.This then tells you the download doesn't have any file corruption.

The files you are running the md5sum on are different.The one called KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5 probably contains the md5sum for the .iso file.

Post output of that directory of ```
ls -lh
``` and what does ```
cat KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
``` show you.
It probably contains the correct value shown by ```
md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
c29e505256e84ccb1943d92b6e6c5b24  KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
```


Good Luck

I was expecting these 2 lines to have matching numbers. 

```
~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
7559dbd329d8afeab1b54bf23d64eaef  KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
c29e505256e84ccb1943d92b6e6c5b24  KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $
```

The download website didn't give me the md5 numbers. Here is all the stuff put together with what you said to do. 
[http://www.knoppix.net/get.php](http://www.knoppix.net/get.php)
[http://torrent.unix-ag.uni-kl.de/](http://torrent.unix-ag.uni-kl.de/)
```

 ~ $ cd /home/bob/Desktop/KN*
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ ls
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5.asc
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.sha1
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.sha1.asc
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso

c29e505256e84ccb1943d92b6e6c5b24  KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ 
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
7559dbd329d8afeab1b54bf23d64eaef  KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ md5sum KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
c29e505256e84ccb1943d92b6e6c5b24  KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ ls -lh
total 3.7G
-rwxrwxrwx 1 bob bob 3.7G 2010-06-06 05:23 KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
-rwxrwxrwx 1 bob bob   70 2010-06-06 05:11 KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
-rwxrwxrwx 1 bob bob  314 2010-06-06 05:11 KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5.asc
-rwxrwxrwx 1 bob bob   78 2010-06-06 05:11 KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.sha1
-rwxrwxrwx 1 bob bob  322 2010-06-06 05:11 KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.sha1.asc
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ cat KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso.md5
c29e505256e84ccb1943d92b6e6c5b24 *KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ md5sum -c KNOPPIX*.iso.md5
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso: OK
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ sha1sum -c KNOPPIX*.iso.sha1
KNOPPIX_V6.2.1DVD-2010-01-31-EN.iso: OK
 ~/Desktop/KNOPPIX_V6.2.1DVD-2010-01-31-EN $ 

```

---

### Post by Ryan Dwyer on 2010-06-13
They match - you'll all good.

There's no point running md5sum on the .md5 file. That file contains the target md5sum you want to see when you md5sum the iso.

---

