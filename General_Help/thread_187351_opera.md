---
title: "opera"
date: 2006-06-02
forum: General Help
---

### Post by nix4me on 2006-06-02
Has anyone gotten opera to install on dapper?

I tried the deb from opera.com but there was a dependancy problem.

nix4me

---

### Post by xXx 0wn3d xXx on 2006-06-02
[QUOTE=nix4me]Has anyone gotten opera to install on dapper?

I tried the deb from opera.com but there was a dependancy problem.

nix4me[/QUOTE]
A dependancy problem with what ? I also had the message "Dependancy problem" but I went ahead and installed it and it worked. Try automatix if that doesn't work.

---

### Post by nix4me on 2006-06-02
xlib6g and xlibs


nix4me

---

### Post by xXx 0wn3d xXx on 2006-06-02
[QUOTE=nix4me]xlib6g and xlibs


nix4me[/QUOTE]
Try:
> wget [http://www.artfiles.org/ubuntu.com/archive/pool/main/x/xorg/xlibs_6.8.2-77_all.deb](http://www.artfiles.org/ubuntu.com/archive/pool/main/x/xorg/xlibs_6.8.2-77_all.deb)
sudo dpkg -i xlibs_6.8.2-77_all.deb
If that doesn't work try installing anyway.

---

### Post by nix4me on 2006-06-02
i got it working.

The xlibs was unnessary.  Even though dpkg complains of unmet dependancies, it still install and runs.  Update manager is complaining now though about a bad count.


nix4me

---

### Post by joshrobinson on 2006-06-02
[QUOTE=nix4me]i got it working.

The xlibs was unnessary.  Even though dpkg complains of unmet dependancies, it still install and runs.

nix4me[/QUOTE]

have you seen a source tarball or amd64 package for opera in your travels?

---

### Post by xXx 0wn3d xXx on 2006-06-02
[QUOTE=joshrobinson]have you seen a source tarball or amd64 package for opera in your travels?[/QUOTE]
Opera is closed source so they wouldn't release the sources code and I don't think an AMD64 package is avaible. I check a few sites including Debian's packages.

---

### Post by joshrobinson on 2006-06-02
[QUOTE=MasterChief1234]Opera is closed source so they wouldn't release the sources code and I don't think an AMD64 package is avaible. I check a few sites including Debian's packages.[/QUOTE]

i just always see people ranting about how good it is.. guess i wont be able to check it out unless i find a package floating around somewhere.. i didnt know it was closed source.. thanks

---

### Post by tenn on 2006-06-02
I had the same problems with xlib6g, but I got Opera installed with all plugins working by downloading the **opera-8.54-20060330.6-shared-qt.i386-en.tar.gz** package from the opera web site.
Than install **libmotif3** and **lesstif2 **
Extracted and ran opera installer
started Opera and set the java path to **/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386**
flash was already working.

---

### Post by RRS on 2006-06-02
Installed about 15 minutes ago using the first two posts in [this thread.]("http://www.ubuntuforums.org/showthread.php?t=177449&highlight=opera")

Definitely fast, now to learn features and how to configure to my liking.

---

### Post by kohoutec on 2006-06-03
The latest weekly build solves the dependancies problem I think. Get it from [http://snapshot.opera.com/unix/Weekly-315/intel-linux/](http://snapshot.opera.com/unix/Weekly-315/intel-linux/) :)

---

### Post by PhilB on 2006-06-03
Thanks for that link MasterChief. Needed xlibs in order to run Bibble, and the packages I found via googling did not iwork.
Phild

---

