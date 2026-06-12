---
title: "how do I install world of goo from tarball"
date: 2011-07-19
forum: General Help
---

### Post by christopher.wortman on 2011-07-19
I purchased it a long time ago, I have the actual PC CD-Rom disk and it contains no DEB file, just a tarball. When extracted I see no install files or make files. 

folders:Icons Libs Properties res
files:eula.txt icon.png linux-issues.txt readme.html WorldOfGoo WorldOfGoo.bin

there is nothing in the txt files that tells me how to actually run and play the game on Linux.

---

### Post by Enigmapond on 2011-07-19
Why are you dealing with a tarball when there is a perfectly good .deb file to install it with?

[http://www.worldofgoo.com/dl2.php?lk=demo&filename=WorldOfGooDemo.1.41.deb](http://www.worldofgoo.com/dl2.php?lk=demo&filename=WorldOfGooDemo.1.41.deb)

---

### Post by christopher.wortman on 2011-07-19
> **Enigmapond said:**
> Why are you dealing with a tarball when there is a perfectly good .deb file to install it with?

[http://www.worldofgoo.com/dl2.php?lk=demo&filename=WorldOfGooDemo.1.41.deb](http://www.worldofgoo.com/dl2.php?lk=demo&filename=WorldOfGooDemo.1.41.deb)

Thats just the demo, I have the disk with the full game on it.

---

### Post by raja.genupula on 2011-07-19
> **christopher.wortman said:**
> I purchased it a long time ago, I have the actual PC CD-Rom disk and it contains no DEB file, just a tarball. When extracted I see no install files or make files. 

folders:Icons Libs Properties res
files:eula.txt icon.png linux-issues.txt readme.html WorldOfGoo WorldOfGoo.bin

there is nothing in the txt files that tells me how to actually run and play the game on Linux.
in the list you mention you have a file called WorldOfGoo.bin.
cd to that folder and then do this, line by line 
```

chmod +x filename.bin
./filename.bin
```

---

### Post by christopher.wortman on 2011-07-19
> **raja.genupula said:**
> in the list you mention you have a file called WorldOfGoo.bin.
cd to that folder and then do this, line by line 
```

chmod +x filename.bin
./filename.bin
```

Thank you that worked great!

---

