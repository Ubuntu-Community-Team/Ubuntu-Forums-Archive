---
title: "Link to editing /home."
date: 2010-10-22
forum: General Help
---

### Post by thebarisaxkid on 2010-10-22
I can't seem to find the thread that gives a guide on how to move the /home folder to second drive.  Can someone send the link if they find it?  

Greatly appreciated.

---

### Post by jerrrys on 2010-10-23
check it out

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=seperate+home+folder&as_qdr=all&sa=Google+Search&lang=en#1113](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=seperate+home+folder&as_qdr=all&sa=Google+Search&lang=en#1113)

---

### Post by oldfred on 2010-10-23
I saved three versions, essentially the same but using different commands to do the copy.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)
cp without -a and copying as sudo root takes ownership (not good)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by thebarisaxkid on 2010-10-23
Thanks!

---

