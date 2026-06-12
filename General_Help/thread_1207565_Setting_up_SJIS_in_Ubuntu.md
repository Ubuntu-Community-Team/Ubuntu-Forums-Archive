---
title: "Setting up SJIS in Ubuntu"
date: 2009-07-08
forum: General Help
---

### Post by umarsaid on 2009-07-08
Simply put, I have two computers. One is Windows XP Japanese and the other is Ubuntu 9.04. When I transfer files in Japanese kanji by using WinSCP to Ubuntu box, I can see the filename kanji from my Windows box, but it becomes mojibake in Ubuntu box.

I have tried tips from this two links below, but none of them works.
[http://ubuntuforums.org/showthread.php?t=382505&highlight=Shift-JIS](http://ubuntuforums.org/showthread.php?t=382505&highlight=Shift-JIS)
[http://ubuntuforums.org/showthread.php?t=383628](http://ubuntuforums.org/showthread.php?t=383628)

Here is my system "locale -a" output (I omitted some unrelated locales).

ar_AE.utf8
C
en_GB.utf8
en_US.utf8
id_ID.utf8
ja_JP
ja_JP.eucjp
ja_JP.sjis
ja_JP.utf8
ko_KR.euckr
ko_KR.utf8
POSIX
zh_CN
zh_CN.gb18030
zh_CN.gbk
zh_CN.utf8
zh_TW
zh_TW.utf8


Notes:
By using samba share folder to transfer files or forcing WinSCP to use UTF-8 encoding, I can transfer files to Ubuntu box and preserving the filenames. But I do not want to do neither of them. What I want is to have my Ubuntu (and Linux as a general) box to recognize Shift-JIS encoding. Is it possible?

---

### Post by jpeddicord on 2009-07-11
Moved to General Help. Tutorials & Tips is not a forum for posting questions.

Jacob

---

