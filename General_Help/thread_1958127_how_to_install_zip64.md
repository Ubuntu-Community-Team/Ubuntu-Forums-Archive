---
title: "how to install zip64?"
date: 2012-04-13
forum: General Help
---

### Post by sohlinux on 2012-04-13
Hi, Anyone tried zip64 for compressing and password protecting files larger than 4gb?

how do I install and use zip64?

thanks

---

### Post by oldos2er on 2012-04-13
If you're running 64-bit Ubuntu, zip should already have this capability.

---

### Post by sohlinux on 2012-04-14
it doesnt work, it comes up with an error when it reaches 4gb in size but I am using 64 bit ubuntu

$ zip -e -r folder01 folder01

zip I/O error: No such file or directory
zip error: Input file read failure (was zipping folder01/54/151.doc)


--

---

### Post by callmemahavir on 2012-04-14
Refer this URL...

[http://superuser.com/questions/319562/linux-zip-greater-than-4gb](http://superuser.com/questions/319562/linux-zip-greater-than-4gb)

---

### Post by sohlinux on 2012-04-14
> **callmemahavir said:**
> Refer this URL...

[http://superuser.com/questions/319562/linux-zip-greater-than-4gb](http://superuser.com/questions/319562/linux-zip-greater-than-4gb)

fine but how do I upgrade to zip64

---

### Post by raja.genupula on 2012-04-14
[http://www.ubuntuupdates.org/package/core/natty/universe/base/p7zip-full](http://www.ubuntuupdates.org/package/core/natty/universe/base/p7zip-full)

click at APT install

---

### Post by callmemahavir on 2012-04-14
7z tool already has a ZIP64 support.

Refer the URL

[http://manpages.ubuntu.com/manpages/oneiric/man1/7z.1.html](http://manpages.ubuntu.com/manpages/oneiric/man1/7z.1.html)

---

### Post by sohlinux on 2012-04-14
I did it with rar and unrar in the end

rar a -pmake_password_here archive.rar dir/

unrar e archive.rar

---

### Post by oldos2er on 2012-04-14
I'm running 12.04, but I think 11.10 would have the same version of zip, 3.0.```
[ann@ann-XPS-410]$ zip -v
Copyright (c) 1990-2008 Info-ZIP - Type 'zip "-L"' for software license.
This is Zip 3.0 (July 5th 2008), by Info-ZIP.
Currently maintained by E. Gordon.  Please send bug reports to
the authors using the web page at www.info-zip.org; see README for details.

Latest sources and executables are at ftp://ftp.info-zip.org/pub/infozip,
as of above date; see http://www.info-zip.org/ for other sites.

Compiled with gcc 4.6.1 for Unix (Linux ELF) on Jun 11 2011.

Zip special compilation options:
        USE_EF_UT_TIME       (store Universal Time)
        BZIP2_SUPPORT        (bzip2 library version 1.0.6, 6-Sept-2010)
            bzip2 code and library copyright (c) Julian R Seward
            (See the bzip2 license for terms of use)
        SYMLINK_SUPPORT      (symbolic links supported)
        LARGE_FILE_SUPPORT   (can read and write large files on file system)
        ZIP64_SUPPORT        (use Zip64 to store large files in archives)
        UNICODE_SUPPORT      (store and read UTF-8 Unicode paths)
        STORE_UNIX_UIDs_GIDs (store UID/GID sizes/values using new extra field)
        UIDGID_NOT_16BIT     (old Unix 16-bit UID/GID extra field not used)
        [encryption, version 2.91 of 05 Jan 2007] (modified for Zip 3)

Encryption notice:
        The encryption code of this program is not copyrighted and is
        put in the public domain.  It was originally written in Europe
        and, to the best of our knowledge, can be freely distributed
        in both source and object forms from any country, including
        the USA under License Exception TSU of the U.S. Export
        Administration Regulations (section 740.13(e)) of 6 June 2002.

Zip environment options:
             ZIP:  [none]
          ZIPOPT:  [none]
```

---

