---
title: "pdf files, windows, ubuntu"
date: 2010-02-15
forum: General Help
---

### Post by fwin on 2010-02-15
Hi everyone,

I would like to know why PDF files take longer (way longer) to open in ubuntu than in windows7?

Am i missing a driver or something?. I have tried to install all kinds of pdf programs like foxit, acrobat, etc... and apparently the best one is foxit but still it is slower than doing it in windows.

Windows opens a particular file in about 10 seconds and ubuntu takes about 2min for the same file, and sometimes more, dont know exactly how much longer because i just kill the process after 2 min. 

I currently have ubuntu 9.10

Is there any way to fix this?. Any help would be appreciated.

---

### Post by saif_held on 2010-02-15
I don't have that problem to be honest and I use the reader that came by default [pre-installed] in Ubuntu. Are you accessing the files from the partitions such as FAT or NTFS? Because I did notice that when I access such files from such drives it take a little, really a little time longer.

---

### Post by fwin on 2010-02-15
thanks for replying,

no i am not accessing any ntfs partitions or anything the file is just in both computers, one with unbuntu and one with windows7? 

The computer with ubuntu is a dell optiplex gx270 with 2gb of ram and 1 core @2.8ghz (with hyper-threading enabled) and the one with win7 is an hp pavillion 752n with 2.8ghz and 1gb of ram (no hyper-threading on this one). I have also tried to disable hyper-threading for the dell and it does not make a difference.

In the dell computer i have another hard drive with win xp and still xp  opens it faster not as fast as the hp with win7 but faster than ubuntu.

The pdf file is 11.4mb, is that too big? I am confused?:confused:

---

### Post by saif_held on 2010-02-15
No, 11.4 Mgb isn't huge. I just opened a 28 Mgb PDF in less than 2 seconds...

That is confusing..I'm sorry for not being helpful :S

---

### Post by fwin on 2010-02-15
saif_held,

 i really appreciate your help, and dont be sorry you were definitely helpful. 


thanks again:D

---

### Post by fwin on 2010-02-15
I just found out that OKULAR does not take that long (it is probably faster than foxit in win7). 

I believe the problem was the visual effects that the pdf file has. Probably the linux version of ACROBAT, EVINCE and FOXIT needs to be upgraded because apparently they can't handle these visual effects.

---

### Post by anoop999 on 2010-02-15
I think there are problems with Evince, the PDF viewer in GNOME. On my system it cannot anti-alias monochrome bitmaps (e.g. scanned documents). I use SumatraPDF on wine which is very fast, but does not allow you to select or copy text. You could also try FoxitReader or Adobe Acrobat or Okular/KPDF.

---

### Post by polki@mac.com on 2010-02-16
I like xpdf. I know it isn't the most snazzy looking piece of code, but it's lightning fast.

---

