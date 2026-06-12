---
title: "Problem opening JPG images"
date: 2011-08-03
forum: General Help
---

### Post by linuxuser12345 on 2011-08-03
Hey, I just popped in a CD for my friend filled with JPEG images to put online, and I get an error message for each picture. This is what pops up:
```
[SIZE=2]**Could not load image 'P1070908.JPG'.**[/SIZE]
Error interpreting JPEG image file (Not a JPEG file: starts with 0x62 0x6f)
```

Can anyone help me out? :( Thank you

---

### Post by LMP900 on 2011-08-03
Hi, could you drag the image to your home folder and run:
```
file P1070908.JPG
```

And post the output.

---

### Post by fdrake on 2011-08-03
check this thread. these may not be jpg images at all but html code instead!
[http://ubuntuforums.org/showthread.php?t=591695](http://ubuntuforums.org/showthread.php?t=591695)

---

### Post by linuxuser12345 on 2011-08-04
```
P1070908.JPG: data
```

---

### Post by fdrake on 2011-08-04
that's why you cannot open it . if it was an image it would say image file.

---

### Post by Wim Sturkenboom on 2011-08-04
Something like below should have been the result

```

wim@ubuntu-desktop01:~# file /usr/share/app-install/icons/_usr_share_pixmaps_jmeter.jpg 
/usr/share/app-install/icons/_usr_share_pixmaps_jmeter.jpg: **JPEG image data, JFIF standard 1.01**
wim@ubuntu-desktop01:~# 

```

---

### Post by linuxuser12345 on 2011-08-05
Is there a way I can convert them from data to image?

---

### Post by fdrake on 2011-08-05
> **linuxuser12345 said:**
> Is there a way I can convert them from data to image?

how did you exactly got those image ? online?

---

### Post by Wim Sturkenboom on 2011-08-06
> **linuxuser12345 said:**
> Is there a way I can convert them from data to image?Not really; they're probably not images in the first place.

You can try to use hd to find out what they are.

```

fortyfourgalena@desktop-01:~$ hd /photos/fortyfourgalena/cat_20110111/IMGP2305.jpg |less
00000000  ff d8 ff e0 00 10 4a 46  49 46 00 01 01 00 00 01  |......JFIF......|
00000010  00 01 00 00 ff e1 4d 1c  45 78 69 66 00 00 4d 4d  |......M.Exif..MM|
00000020  00 2a 00 00 00 08 00 07  00 0b 00 02 00 00 00 0b  |.*..............|
00000030  00 00 00 62 01 0f 00 02  00 00 00 14 00 00 00 6e  |...b...........n|
00000040  01 10 00 02 00 00 00 14  00 00 00 82 01 12 00 03  |................|
00000050  00 00 00 01 00 01 00 00  01 31 00 02 00 00 00 18  |.........1......|
00000060  00 00 00 96 01 32 00 02  00 00 00 14 00 00 00 ae  |.....2..........|
00000070  87 69 00 04 00 00 00 01  00 00 00 c2 00 00 32 e8  |.i............2.|
00000080  55 46 52 61 77 20 30 2e  31 36 00 00 50 45 4e 54  |UFRaw 0.16..PENT|
00000090  41 58 20 43 6f 72 70 6f  72 61 74 69 6f 6e 20 00  |AX Corporation .|
000000a0  50 45 4e 54 41 58 20 4b  31 30 30 44 20 20 20 20  |PENTAX K100D    |
000000b0  20 20 20 00 4b 31 30 30  44 20 20 20 20 20 20 20  |   .K100D       |
000000c0  56 65 72 20 31 2e 30 32  20 20 20 00 32 30 31 31  |Ver 1.02   .2011|
000000d0  3a 30 31 3a 31 31 20 31  38 3a 33 36 3a 30 30 00  |:01:11 18:36:00.|
000000e0  00 19 82 9a 00 05 00 00  00 01 00 00 01 f4 82 9d  |................|
000000f0  00 05 00 00 00 01 00 00  01 fc 88 22 00 03 00 00  |..........."....|

```The first few lines should look like above; if there is similarity in yours (e.g. jfif, exif, camera name), it might be possible; maybe photorec can do it in that case.

---

### Post by fdrake on 2011-08-06
you could use also photorecover (i don't know if it's the same program that Wim is suggesting)..
link [http://www.ee.oulu.fi/~iiska/projects/photorecover/](http://www.ee.oulu.fi/~iiska/projects/photorecover/)

---

