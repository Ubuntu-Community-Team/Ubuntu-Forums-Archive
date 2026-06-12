---
title: "Error while installing MAgic layout tool"
date: 2012-04-06
forum: General Help
---

### Post by emmagood on 2012-04-06
Hi,

 I am trying to install Magic layout tool for VLSI. When I do ./ configure and make, the process is OK without error. But when I do "make install" I get the following error:

--- installing executable to /usr/local/bin
--- installing runtime files to /usr/local/lib
rm: cannot remove `windows7.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows7.glyphs': Permission denied
rm: cannot remove `windows11.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows11.glyphs': Permission denied
rm: cannot remove `windows14.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows14.glyphs': Permission denied
rm: cannot remove `windows22.glyphs': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/windows22.glyphs': Permission denied
make[2]: *** [install-tcl] Error 1
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.std.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.24bit.dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.24bit.std.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.mraster_dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.7bit.mraster.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.OpenGL.dstyle': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/mos.OpenGL.std.cmap': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/minimum.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/gdsquery.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmos.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmos-tm.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmos-sub.tech': Permission denied
cp: cannot create regular file `/usr/local/lib/magic/sys/scmosWR.tech': Permission denied
make[2]: *** [install-tcl] Error 1
rm: cannot remove `/usr/local/bin/magic': Permission denied
make[2]: *** [/usr/local/bin/magic.sh] Error 1
/usr/bin/ld: cannot find -lXmu
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make[2]: *** [tclmagic.so] Error 1
rm: cannot remove `/usr/local/bin/magic': Permission denied
make[2]: *** [/usr/local/bin/magic.sh] Error 1
make[1]: *** [install-tcl-real] Error 2
make: *** [install-tcl] Error 2


 I tried by "sudo make install" as in the solution ([http://ubuntuforums.org/showthread.php?t=826420](http://ubuntuforums.org/showthread.php?t=826420)) but it did not help. How can i go about the problem without having to reinstall ubuntu. 

Thanks,
Emma Good.

---

### Post by Toz on 2012-04-06
Hello and welcome to the forums.

What error message(s) do you get when you try with:
```
sudo make install
```

What version of ubuntu are you using?

I just succesfully built the package on 11.10 using:
```
./configure
make
sudo make install
```

I needed to install the following packages for it to work:
- tlc8.5-dev
- tk8.5-dev
- csh

---

### Post by emmagood on 2012-04-06
Hi,

  I had installed the tcl and csh packages along with the other required packages mentioned on magic installation site. ([http://opencircuitdesign.com/magic/install.html](http://opencircuitdesign.com/magic/install.html)). The error for sudo make install are :

--- installing executable to /usr/local/bin
--- installing runtime files to /usr/local/lib
/usr/bin/ld: cannot find -lXmu
/usr/bin/ld: cannot find -lstdc++
collect2: ld returned 1 exit status
make[2]: *** [tclmagic.so] Error 1

 I am also on Ubuntu 11


Thanks,

 Emma Good

---

### Post by emmagood on 2012-04-07
Update:

lXmu issue was solved by installing the appropriate library:

sudo apt-get install libxmu-dev libxmu6


any ideas of the corresponding lstdc++ library



Thanks.

---

### Post by emmagood on 2012-04-07
The issue was resolved by sudo apt-get install build-essential


Thanks,

Emma Good.

---

