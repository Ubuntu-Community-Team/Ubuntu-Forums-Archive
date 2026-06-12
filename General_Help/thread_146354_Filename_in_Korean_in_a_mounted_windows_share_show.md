---
title: "Filename in Korean in a mounted windows share show up as &quot;????&quot;"
date: 2006-03-18
forum: General Help
---

### Post by bhishma on 2006-03-18
When I access a Windows share directly thorough Nautilus by typing "smb://..." in the address bar, there is no problem.  All files, even those with names in Korean alphabet, are displayed correctly.

But when I mount the share (auto-mount through fstab), and when I navigate to the mounted location, the file names in Korean alphabet break up, each syllable being replaced by a question mark.

For example, &#54028;&#51068; &#51060;&#47492; -> "?? ??"

What is the problem? How can I solve this?

---

### Post by Sutekh on 2006-03-19
Try adding ```
iocharset=utf8
``` to the smb mount entry if the share is formatted FAT32

Try adding ```
nls=utf8
``` to the smb mount entry if the share is formatted NTFS

---

### Post by baytuni on 2006-12-11
I have a similar problem but the mounted drive is a local drive and the language is Turkish. Especially I have trouble with mp3 files not being recognized by media players. I tried the above solution but nothing had changed. Have you got any recommendations?

---

### Post by annda on 2006-12-11
if you can, you can try convmv to recode the filenames into UTF-8 - it's in the repositories, so do simply:

```
sudo apt-get install convmv
```

more info on the [homepage]("http://j3e.de/linux/convmv/")

and it this [article]("http://www.linux.com/article.pl?sid=06/11/27/1549236") on linux.com

---

