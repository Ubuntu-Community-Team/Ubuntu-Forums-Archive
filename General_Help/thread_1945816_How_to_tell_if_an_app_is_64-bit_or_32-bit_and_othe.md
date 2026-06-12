---
title: "How to tell if an app is 64-bit or 32-bit and other instalation difficulties"
date: 2012-03-23
forum: General Help
---

### Post by 7o7YlUcb on 2012-03-23
I am trying to install a fairly obscure piece of software called GRASS. I made various attempts to install it from various sources. It did not appear in 'dash-home' so I assumed all my attempts at installation were unsuccessful. However when I typed 'grass' in the terminal it appeared. (As you've probably worked by now out I'm not very competent with Linux). The thing is I dont know which of my attempts was the one that worked so I dont know if it is a 32 or 64-bit version of GRASS.

1) Is there a way to 'ask' the application if it is a 32 or 64-bit software? Or can you figure this out by looking at where it is installed.

2) Is there a flag or something I can use for the apt-get install (or whatever) to make it install in a different folder if I need several versions of the same software?

3) I may have to attempt to install it by compiling some source. Will it compile as a 64bit app by default as I have a 64-bit OS or will I need to edit the installation script

I'm on Ubuntu 11.10 64-bit.

Thanks.

---

### Post by jerome1232 on 2012-03-23
If you installed it via the package manager then dpkg will know about it, so try asking dpkg (this will provide information about the architecture as well)

```
dpkg-query -s grass
```

---

### Post by Yellow Pasque on 2012-03-23
1) Maybe:
```
file `which grass`
```

2) If building from source, you can usually use the --prefix flag. If installing from apt/.deb, then the path is predetermined.

3) It should build 64-bit automatically (unless you pass configure flags)

---

### Post by jerome1232 on 2012-03-23
> **Temüjin said:**
> 1) Maybe:
```
file `which grass`
```

Is there a typo in that command? (it wouldn't work on my system)

---

### Post by Yellow Pasque on 2012-03-23
If you don't have grass, then it won't work. Also, note those are backticks (Shift + ~), not apostrophes.

---

### Post by jerome1232 on 2012-03-23
sneaky backticks

---

### Post by 7o7YlUcb on 2012-03-23
Thanks for all your answers.

"dpkg-query -s grass" Says "Architecture: amd64".

Just to be clear, can you someone confirm that this is saying that it is the GRASS software that is amd64 (and not the OS or anything)? (The manual on this command doesnt really explain it.)
 
```
Package: grass
Status: install ok installed
Priority: optional
Section: science
Installed-Size: 41568
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 6.4.1-1build1
Provides: grass641
Depends: lesstif2 (>= 1:0.94.4), libc6 (>= 2.11), libcairo2 (>= 1.6.0), libfftw3-3, libfreetype6 (>= 2.2.1), libgcc1 (>= 1:4.1.1), libgdal1-1.7.0, libgl1-mesa-glx | libgl1, libglu1-mesa | libglu1, libmysqlclient16 (>= 5.1.50-1), libncurses5 (>= 5.5-5~), libpng12-0 (>= 1.2.13-4), libpq5 (>= 8.4~), libproj0, libreadline6 (>= 6.0), libsqlite3-0 (>= 3.5.9), libstdc++6 (>= 4.4.0), libtiff4, libx11-6, libxmu6, libxt6, tcl8.5 (>= 8.5.0), tk8.5 (>= 8.5.0), unixodbc (>= 2.2.11), zlib1g (>= 1:1.1.4), xterm | x-terminal-emulator, python (>= 2.5), python-numpy, python-opengl, python-wxgtk2.8
Recommends: ghostscript
Suggests: grass-doc, gdal-bin, proj-bin, e00compr, avce00, gpsbabel, gpstrans, gnuplot, xml2, wget | curl, netpbm
Description: Geographic Resources Analysis Support System
 Commonly referred to as GRASS, this is a Geographic Information
 System (GIS) used for geospatial data management and analysis,
 image processing, graphics/map production, spatial modeling, and
 visualization. GRASS is currently used in academic and commercial
 settings around the world, as well as by many government agencies
 and environmental consulting companies.
Original-Maintainer: Debian GIS Project <pkg-grass-devel@lists.alioth.debian.org>
Homepage: http://grass.osgeo.org/
```

---

### Post by wildmanne39 on 2012-03-23
Hi, that is what it looks like it is saying to me.
Thanks

---

### Post by jerome1232 on 2012-03-23
Yeah, it's the package that's amd64. Logically, dpkg is describing the package, not the OS it's installed in.

---

### Post by Yellow Pasque on 2012-03-23
If the package had 32-bit binaries, it would depend on ia32-libs.

---

