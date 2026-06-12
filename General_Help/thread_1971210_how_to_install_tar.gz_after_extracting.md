---
title: "how to install tar.gz after extracting?"
date: 2012-05-02
forum: General Help
---

### Post by shazej on 2012-05-02
hi guys im new to ubuntu.but hav used it a lil .i need your help on installing a tar.gz file which i downloaded from net.i just extracted it using archieve manager.now i dont know what to do.

---

### Post by marrok1 on 2012-05-02
As i do not know exactly the contents of the directory you just uncompressed ill just take a shot in the dark here.

1) cd into the extracted directory
2) sudo ./configure
3) sudo make
4) sudo make install

---

### Post by shazej on 2012-05-02
> **marrok1 said:**
> As i do not know exactly the contents of the directory you just uncompressed ill just take a shot in the dark here.

1) cd into the extracted directory
2) sudo ./configure
3) sudo make
4) sudo make install
my tar.gz extracted file is on my desktop.can u say how to cd there.
when i type cd home/home/desktop/aircrack-ng-1.1
they say there is no such file or directory

---

### Post by mikejonesey on 2012-05-02
there isn't, Desktop not desktop! lol

```
find . -maxdepth 1 -iname "desktop" | xargs ls | grep -i "aircr" | while read dn; do cd $dn; echo "The directory you want is... `pwd`"; done 
```

---

### Post by drmrgd on 2012-05-02
> **shazej said:**
> hi guys im new to ubuntu.but hav used it a lil .i need your help on installing a tar.gz file which i downloaded from net.i just extracted it using archieve manager.now i dont know what to do.

What I would recommend is to look for a README file or INSTALL text file or some such in the directory that you extracted with the archive manager.  If there is one there, it will lay out the exact instructions for how to install and compile the program.  

Also, it looks like the software is in the [repos for Oneiric]("http://packages.ubuntu.com/oneiric/aircrack-ng"), and you could just install it with the software manager if you've not yet updated your system to v12.04. That'll make things a bit easier.  If you have already upgraded, you'll probably have to go the manual compile route.

---

### Post by Cheesemill on 2012-05-02
I don't think you'll get any help here.

Discussion of the installation and use of aircrack is not allowed on these forums.

Try asking for help at the BackTrack forums instead:
[http://www.backtrack-linux.org/forums](http://www.backtrack-linux.org/forums)

---

### Post by nothingspecial on 2012-05-02
Questions on aircrack-ng are better asked either on the backtrack forums linked above or the aircrack forums.

[http://forum.aircrack-ng.org/](http://forum.aircrack-ng.org/)

Closed.

---

