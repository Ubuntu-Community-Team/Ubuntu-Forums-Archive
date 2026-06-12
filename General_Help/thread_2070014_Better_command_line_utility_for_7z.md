---
title: "Better command line utility for 7z?"
date: 2012-10-11
forum: General Help
---

### Post by Stonecold1995 on 2012-10-11
Are there any command line utilities to open .7z files that are a little more intuitive than the current "7z" command?  Because it's quite confusing and acts nothing like other utilities like zip, rar, tar, gzip, bzip2, lha, etc.  Or maybe a script that "converts" the odd syntax used by 7z to more understandable syntax?

---

### Post by oldos2er on 2012-10-11
Not sure if this is what you're looking for, but check out **atool**. It's in the repositories. It can handle many different compression file formats, including 7z (I think you need to install p7zip). According to **atool --help**, it can "repack archives to a different format (arepack)".

I use it to extract various file types, e.g. tar.gz and tar.bz2. Instead of trying (and failing) to remember the various options different formats require, I only need to remember **atool -x foo.tar.bz2**

---

### Post by Stonecold1995 on 2012-10-12
Thank you!  Even better!

---

### Post by 3rdalbum on 2012-10-12
I know you asked for command-line utilities, but File Roller can drive 7z.

---

### Post by Stonecold1995 on 2012-10-13
I use PeaZip for a front-end GUI, or sometimes I'll use the Windows version of 7-zip through Wine.  Does File Roller have more features than those two?

---

