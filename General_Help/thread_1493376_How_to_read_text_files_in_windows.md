---
title: "How to read text files in windows?"
date: 2010-05-25
forum: General Help
---

### Post by murt on 2010-05-25
A real os should at least be able to read and write plain text, you think? But no, when I try to open my text files (mainly made with gedit) some characters are a mess, swedish letters rarely work and ', ", / and so on are not represented as the characters I want to see. 

Is there a easy, fast way to read (and print!) my text files at school, where they have only windows, without spending half an hour fixing the file by hand?

---

### Post by bodhi.zazen on 2010-05-25
1. Try opening the file with wordpad.

2. Look at your encoding.

See this thread (several options) : 

[http://ubuntuforums.org/showthread.php?t=1276333](http://ubuntuforums.org/showthread.php?t=1276333)

---

### Post by jerenept on 2010-05-25
Huh. Sounds like an encoding problem. Maybe you could try 'save as' with Windows line ending. Don't use Windows often, and, use .doc or .rtf (made in open office) so I am not sure.

---

### Post by bodhi.zazen on 2010-05-26
On the Windows side, save as .txt works best.

---

### Post by inso_741 on 2010-05-26
sorry ignore this post

---

### Post by fragos on 2010-05-26
Windows may be using a different character set than Linux, for example utf-8. The basic characters are the same for the most part but special characters for foreign language and fancy left right quotes may be different between the two systems. Also end of line in Linux is a single character CR. Windows uses CR and LF.

---

### Post by 2hot6ft2 on 2010-05-26
> **bodhi.zazen said:**
> 1. Try opening the file with wordpad.

This has always worked for me.

---

