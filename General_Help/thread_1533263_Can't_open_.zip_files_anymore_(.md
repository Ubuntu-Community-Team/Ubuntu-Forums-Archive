---
title: "Can't open .zip files anymore :("
date: 2010-07-17
forum: General Help
---

### Post by Cant on 2010-07-17
When I try to open these things all I get is this message:

```
7-Zip 9.04 beta  Copyright (c) 1999-2009 Igor Pavlov  2009-05-30
p7zip Version 9.04 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)

Error: /home/adam/ctf_floatingforts.zip: Can not open file as archive

Errors: 1
```

I /think/ it happened after an interrupted upgrade to ubuntu 10.10

what is this i dont even

---

### Post by AlphaLexman on 2010-07-17
It appears you are using 7z. Have you tried unzip?

---

### Post by Cant on 2010-07-17
> **AlphaLexman said:**
> It appears you are using 7z. Have you tried unzip?

How do I do that?

---

### Post by oldefoxx on 2010-07-17
Many file types are known by either or both of two methods.  The extension, such as .zip, or the header, which is the leading contents.  The leading  contents may also infer a certain internal structure to the file is required.  You see .zip okay, but 7zio or whatever you are using sees a failure in one of the other two categories,  Now sometimes we have file errors that can cause this, and sometimes it is the extraction program that is at fault.  With so many possibilities, you have to sort of work through the possibilities until you manage to find a solution.  Another zip file extractor, another zip file to test against, might be enough to show you where the problem is.

But this is hands on stuff.  From a distance, we can only say what it might be, not what it really is.  Either you do the hands on, or you find a way and a manner in which it gets done by someone else.

---

### Post by AlphaLexman on 2010-07-17
> **oldefoxx said:**
> Many file types are known by either or both of two methods.  The extension, such as .zip, or the header, which is the leading contents. 
To determine the header of your file, type:
```
file /home/adam/ctf_floatingforts.zip
```To utilize the program 'unzip' type:
```
unzip /home/adam/ctf_floatingforts.zip
```

---

### Post by Cant on 2010-07-17
I've tried a few other .zip files that I know are not corrupted and they all give me the same error. When I try to use unzip it gives me this message:
```
Archive:  fc5.zip
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of fc5.zip or
        fc5.zip.zip, and cannot find fc5.zip.ZIP, period.
```

---

### Post by Cant on 2010-07-18
bump

---

### Post by AlphaLexman on 2010-07-18
What is the output of:
```
file yourcompressed.zip
```
and,
```
zipinfo yourcompressed.zip
```

---

### Post by Cant on 2010-07-18
> **AlphaLexman said:**
> What is the output of:
```
file yourcompressed.zip
```
and,
```
zipinfo yourcompressed.zip
```

```
Zip archive data, at least v2.0 to extract
```
and
```
End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/adam/ctf_floatingforts.zip or
          /home/adam/ctf_floatingforts.zip.zip, and cannot find /home/adam/ctf_floatingforts.zip.ZIP, period.
```

---

### Post by AlphaLexman on 2010-07-18
What is the source of the .zip file?
Did it come from another OS? (win, mac, etc.)
Is it part of a larger backup? (multiple .zip(s) to fit on a disc maybe?)
Is the file corrupt or encrypted?
Do you have the right permissions?

---

### Post by Cant on 2010-07-18
> **AlphaLexman said:**
> What is the source of the .zip file?
Did it come from another OS? (win, mac, etc.)
Is it part of a larger backup? (multiple .zip(s) to fit on a disc maybe?)
Is the file corrupt or encrypted?
Do you have the right permissions?
It's a map for Sauerbraten from Quadropolis.us, it's probably from a Windows computer but I can't know for certain. It's not a part of a larger backup, it's not corrupted/encrypted and I have the right permissions.

---

### Post by AlphaLexman on 2010-07-18
Could you post a link to the file from Quadropolis.us? I could try it.

---

### Post by Cant on 2010-07-18
> **AlphaLexman said:**
> Could you post a link to the file from Quadropolis.us? I could try it.

I tested these:
[http://quadropolis.us/node/2718](http://quadropolis.us/node/2718)
[http://quadropolis.us/node/1352](http://quadropolis.us/node/1352)

---

### Post by AlphaLexman on 2010-07-18
> [http://quadropolis.us/node/1352](http://quadropolis.us/node/1352)```
zipinfo ctf_floatingforts.zip
```Gave me this:
```
Archive:  ctf_floatingforts.zip
Zip file size: 947570 bytes, number of entries: 6
-rw-a--     2.0 fat      105 t- defN 08-Jun-02 21:38 readme.txt
drwx---     2.0 fat        0 b- stor 08-Jun-02 21:45 packages/base/
-rw-a--     2.0 fat     9370 t- defN 08-May-26 00:20 packages/base/ctf_floatingforts.cfg
-rw-a--     2.0 fat   850076 b- defN 08-Jun-02 22:03 packages/base/ctf_floatingforts.ogz
-rw-a--     2.0 fat    48708 b- defN 08-Jun-03 11:56 cft_floatingforts.jpg
-rw-a--     2.0 fat    48708 b- defN 08-Jun-03 11:56 packages/base/cft_floatingforts.jpg
6 files, 956967 bytes uncompressed, 946792 bytes compressed:  1.1%

```and,
```
md5sum ctf_floatingforts.zip
84a0a91aa18377e0d2a818a45d0d76f2  ctf_floatingforts.zip
```
> [http://quadropolis.us/node/2718](http://quadropolis.us/node/2718)```
zipinfo fc5.zip
```Gave me this:
```
Archive:  fc5.zip
Zip file size: 4089532 bytes, number of entries: 12
drwx---     2.0 fat        0 b- stor 10-Jun-20 20:48 packages/
drwx---     2.0 fat        0 b- stor 10-Jun-20 20:49 packages/base/
-rw-a--     2.0 fat    17283 b- defN 10-Jun-06 21:34 packages/base/fc5.cfg
-rw-a--     2.0 fat    34711 b- defN 10-May-30 18:59 packages/base/fc5.jpg
-rw-a--     2.0 fat  3541917 b- defN 10-Jun-20 20:46 packages/base/fc5.ogz
-rw-a--     2.0 fat    26875 b- stor 10-Jun-01 18:58 packages/base/fc5.wpt
-rw-a--     2.0 fat     4215 b- defN 10-Jun-06 21:36 packages/base/readme_fc5.txt
drwx---     2.0 fat        0 b- stor 10-Jun-20 20:48 packages/blindabuser/
-rw-a--     2.0 fat   239284 b- defN 10-May-24 18:09 packages/blindabuser/ba_rooftile_cc.jpg
-rw-a--     2.0 fat   114992 b- defN 10-May-24 17:41 packages/blindabuser/ba_rooftile_hm.jpg
-rw-a--     2.0 fat    74650 b- defN 10-May-24 20:36 packages/blindabuser/ba_rooftile_nm.jpg
-rw-a--     2.0 fat    77672 b- defN 10-May-24 18:02 packages/blindabuser/ba_rooftile_sc.jpg
12 files, 4131599 bytes uncompressed, 4087974 bytes compressed:  1.1%

```and,
```
md5sum fc5.zip 
78ce7ed98a71107183a38b05ecc2bc06  fc5.zip
```I'm guessing you've tried downloading them again?

---

### Post by Cant on 2010-07-18
> **AlphaLexman said:**
> ..I'm guessing you've tried downloading them again?

Well.. No :oops: And it worked, thank you.

---

### Post by aidenscool09 on 2010-07-18
I reccommend you try installing PeaZip. Its really good as it can open just about any compressed file, you may need the plugin for 7zip, but it should work. It isn't in the Ubuntu Repositories. So here is the site [http://peazip.sourceforge.net/](http://peazip.sourceforge.net/)

---

### Post by aidenscool09 on 2010-07-18
O right, sorry about the late post LOL. I didn't realise because I spent the last 10 minutes on my Conky config.

---

