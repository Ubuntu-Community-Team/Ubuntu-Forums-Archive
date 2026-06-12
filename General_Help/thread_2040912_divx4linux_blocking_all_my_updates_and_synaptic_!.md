---
title: "divx4linux blocking all my updates and synaptic !"
date: 2012-08-11
forum: General Help
---

### Post by jeanmarat on 2012-08-11
I can't install or uninstall anything due to divx4linux !

I get this message :


```
dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5440 package 'divx4linux':
 error in Version string '6.1.1_zolerubuntu1': invalid character in version number
dpkg: error: parsing file '/var/lib/dpkg/status' near line 5445 package 'divx4linux':
 blank line in value of field 'Description'
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Here is what /var/lib/dpkg/status has :


> Package: divx4linux
Status: install ok installed
Priority: optional
Section: libraries
Installed-Size: 2560
Maintainer: Lukacs Zoltan  <zolerubuntu@gmail.com>
Architecture: all
Version: 6.1.1_zolerubuntu1
Depends: libc6 (>= 2.7-0), debconf (>= 1.5.20)
Description: DivX codec library and headers for Linux
 After three years of silence, DivX has released on 1 february 2006 it's brand new
 version 6 of the popular codec for Linux. The release was coming out three months
 after the Windows edition and is very stable.
 
 Complete list of news for the Linux codec since version 5.0.5 is available on DivX
 homepage, but here are a few of the highlights:
 
    * Improved bi-directional coding (including multiple adaptive B-frames)
    * Rate-distortion optimized encoding modes ("Better quality", "Extreme quality",
      "Insane quality")
    * Faster decoder and higher quality of post-processing
    * Better support for generic MPEG-4 playback
    * "Fastest" and "High Performance" encoding modes
    * Much improved compression for equivelent quality
    * Optimizations for newer processors
    * Updated VBV for improved support for DivX Certified devices
    * Two psychovisual enhancement modes
    * Quality optimized H.263 quantization method
    * Support for 4MV motion compensation
    * New encoding modes and resize methods.
 
 Known issues:
 
    * Codec libraries must be leveraged from an application calling the API
    * This version does not support multithreading.
 
 This software is copyright (C) 2006 by DivX Inc., but is free for personal use and
 includes DivX Pro features.
 
 Homepage: [http://labs.divx.com/DivXLinuxCodec](http://labs.divx.com/DivXLinuxCodec)


---

### Post by jeanmarat on 2012-08-26
ok thanks to the help of two nice friends i just removed the bulk of the description and changed it to "divx" and now i can install packages !

and try changing "_"  in the version bit with a "-"

---

