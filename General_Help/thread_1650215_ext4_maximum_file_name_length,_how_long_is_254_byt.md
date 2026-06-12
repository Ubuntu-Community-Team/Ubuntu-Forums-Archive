---
title: "ext4 maximum file name length, how long is 254 bytes?"
date: 2010-12-21
forum: General Help
---

### Post by john1923 on 2010-12-21
Hi

In the big bad world of windows vista I lost some files because after moving them their file names were over 255 characters. (NTFS file system)

Ext4 has a Max file name size of 256 bytes, how long is this in characters? I suspect that this depends on how the characters are encoded, but can someone enlighten me?

I am running 64 bit Ubuntu 10.04 LTS

Thank-you.

---

### Post by 3Miro on 2010-12-21
Standard ASCII, this makes 256 characters. If it is Unicode encoding, it would be 256/4 = 64. I just created a filename with over 100 characters (on Gentoo not Ubuntu). You can test that under Ubuntu by making a  file and renaming it with 1234567890. See how many such strings you can fit in the filename.

BTW are you sure it is the size of the filename and not say special characters within the name.

---

### Post by psusi on 2010-12-21
255 bytes is 255 ASCII characters.  Unicode characters are encoded in UTF-8 which is variable length.  Most are 2-3 bytes, with some being 4.

---

### Post by john1923 on 2010-12-21
lol, I'm an experimental scientist and it didn't occur to me to just try...  

perl -e 'print("ls > " ,"A" x 255, "\n" );' | sh

255 is the longest file-name that I can make before I get an error.

---

