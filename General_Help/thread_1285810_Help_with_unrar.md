---
title: "Help with unrar"
date: 2009-10-08
forum: General Help
---

### Post by xx77aBs on 2009-10-08
Hello ! I have problem with .rar archives ...
I need to check (over SSH) if archive is password protected or not ... Is there any command to do that ?

Or maybe I need another program ?

Thanks !

---

### Post by khelben1979 on 2009-10-08
```
ls -l | less *.rar
``` will show information about it's archives, but suspect that it won't show what you're looking for (uncertain). Maybe connecting through the web browser as [web based SSH]("http://en.wikipedia.org/wiki/Web-based_SSH") will simplify what you're after?

---

### Post by xx77aBs on 2009-10-08
no, I still can't see if archive is password protected or not ...

---

### Post by Bachstelze on 2009-10-08
```
for i in *.rar; do unrar x -p- $i &> /dev/null || echo $i; done
```

will try to unrar each rar file in the current directory without a password, and will output the name of the rar file if extraction failed (which will most likely be because the file needed a password).

If you want to check a single file, just try to extract it and see what gives:

```
unrar x -p- file.rar
```

```
firas@iori ~ % unrar x -p- NeroDigitalAudio.zip.rar

UNRAR 3.90 freeware      Copyright (c) 1993-2009 Alexander Roshal


Extracting from NeroDigitalAudio.zip.rar

Extracting  NeroDigitalAudio.zip                                      84%
Encrypted file:  CRC failed in NeroDigitalAudio.zip (password incorrect ?)
Total errors: 1

```

---

### Post by xx77aBs on 2009-10-08
yes, but it's too slow ... I have to check very large number of rars, and unraring them isn't best sollution ...

---

### Post by Bachstelze on 2009-10-08
> **xx77aBs said:**
> yes, but it's too slow ... I have to check very large number of rars, and unraring them isn't best sollution ...

It's the only one.

---

### Post by xx77aBs on 2009-10-08
that's kind of stupid ... in windows you see in GUI if rar is password-protected or not ...

is there any way to start unrar and then close it after few seconds and do that for all other files ?

---

### Post by sedawk on 2009-10-08
You can try "file archive.rar" it might tell you it is
a rar file and even if it is password protected.

You can also try to use 7z instead of "unrar" but anyway
there should be some kind of option to list the content
of the archive or test an archive without unpacking.
This should be fast and as far as I understood listing
the content is only possible when knowing the password.

---

### Post by Bachstelze on 2009-10-08
> **sedawk said:**
> You can try "file archive.rar" it might tell you it is
a rar file and even if it is password protected.

It does say that it's a rar file, but not whether or not it's password protected:

```
firas@iori ~ % rar a ClearfaceSSi.7z.nopassword.rar ClearfaceSSi.7z

RAR 3.90 beta 2   Copyright (c) 1993-2009 Alexander Roshal   3 Jun 2009
Shareware version         Type RAR -? for help

Evaluation copy. Please register.

Creating archive ClearfaceSSi.7z.nopassword.rar

Adding    ClearfaceSSi.7z                                             OK
Done
firas@iori ~ % rar a -pfoo ClearfaceSSi.7z.password.rar ClearfaceSSi.7z

RAR 3.90 beta 2   Copyright (c) 1993-2009 Alexander Roshal   3 Jun 2009
Shareware version         Type RAR -? for help

Evaluation copy. Please register.

Creating archive ClearfaceSSi.7z.password.rar

Adding    ClearfaceSSi.7z                                             OK
Done
firas@iori ~ % file ClearfaceSSi.7z.password.rar
ClearfaceSSi.7z.password.rar: RAR archive data, v1d, os: Unix
firas@iori ~ % file ClearfaceSSi.7z.nopassword.rar
ClearfaceSSi.7z.nopassword.rar: RAR archive data, v1d, os: Unix

```

> **sedawk said:**
> You can also try to use 7z instead of "unrar" but anyway
there should be some kind of option to list the content
of the archive or test an archive without unpacking.
This should be fast and as far as I understood listing
the content is only possible when knowing the password.

Not quite, but close:

```
firas@iori ~ % unrar l ClearfaceSSi.7z.nopassword.rar

UNRAR 3.90 freeware      Copyright (c) 1993-2009 Alexander Roshal

Archive ClearfaceSSi.7z.nopassword.rar

 Name             Size   Packed Ratio  Date   Time     Attr      CRC   Meth Ver
-------------------------------------------------------------------------------
 ClearfaceSSi.7z   135291   135699 100% 13-07-09 17:56 -rw-r--r-- 3A28C02D m3c 2.9
-------------------------------------------------------------------------------
    1           135291   135699 100%

firas@iori ~ % unrar l ClearfaceSSi.7z.password.rar

UNRAR 3.90 freeware      Copyright (c) 1993-2009 Alexander Roshal

Archive ClearfaceSSi.7z.password.rar

 Name             Size   Packed Ratio  Date   Time     Attr      CRC   Meth Ver
-------------------------------------------------------------------------------
*ClearfaceSSi.7z   135291   135712 100% 13-07-09 17:56 -rw-r--r-- 3A28C02D m3c 2.9
-------------------------------------------------------------------------------
    1           135291   135712 100%


```

As you can see, in the password-protected archive, each encrypted file is shown with an asterisk before it. So we can do:

```
firas@iori ~ % for i in *rar; do unrar l $i | egrep "^\*" > /dev/null && echo $i; done
ClearfaceSSi.7z.password.rar

```

which will output the filename of all archives that contain password-protected files.

---

### Post by xx77aBs on 2009-10-08
yes, that's it ... I don't know how I didn't notice * before the file when getting the list of files inside archive :D 

Thanks a million times !!

---

