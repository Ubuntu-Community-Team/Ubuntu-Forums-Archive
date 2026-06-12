---
title: "perl GD module won't install"
date: 2006-04-22
forum: General Help
---

### Post by dbunder on 2006-04-22
with a simple perl -MCPAN -e shell, then install GD

libgd is installed, as it's a default part of the ubuntu install (running badger), all of the libs needed are installed (see my huge code block below).  i have also install gd with xpm support using synaptic.  here's my code block showing the build progress within a CPAN shell.  what am I doing wrong, or what am I missing?  thanks much for any help.  it's essential i get this installed for a project i'm working on.  i know the code block is big, i just wanted to be as verbose as possible.  if you have any questions about anything, just ask and i'll get back to you.  thanks again!!!:-? 

```
Where is libgd installed? [/usr/lib]

Please choose the features that match how libgd was built:
Build JPEG support? [y]
Build PNG support? [y]
Build FreeType support? [y]
Build GIF support? [y]
Build support for animated GIFs? [y]
Build XPM support? [y]

If you experience compile problems, please check the @INC, @LIBPATH and @LIBS
arrays defined in Makefile.PL and manually adjust, if necessary.

Checking if your kit is complete...
Looks good
Writing Makefile for GD
CPAN: YAML loaded ok
/usr/bin/perl "-Iblib/arch" "-Iblib/lib" GD/Image.pm.PLS GD/Image.pm
Extracting Image.pm (with variable substitutions)
cp GD/Polyline.pm blib/lib/GD/Polyline.pm
cp qd.pl blib/lib/qd.pl
cp GD/Image.pm blib/lib/GD/Image.pm
cp GD.pm blib/lib/GD.pm
AutoSplitting blib/lib/GD.pm (blib/lib/auto/GD)
cp GD/Simple.pm blib/lib/GD/Simple.pm
cp GD/Polygon.pm blib/lib/GD/Polygon.pm
/usr/bin/perl /usr/share/perl/5.8/ExtUtils/xsubpp  -typemap /usr/share/perl/5.8/ExtUtils/typemap -typemap typemap  GD.xs > GD.xsc && mv GD.xsc GD.c
cc -c  -I/usr/include -I/usr/include/gd -D_REENTRANT -D_GNU_SOURCE -DTHREADS_HAVE_PIDS -DDEBIAN -fno-strict-aliasing -pipe -I/usr/local/include -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -O2   -DVERSION=\"2.32\" -DXS_VERSION=\"2.32\" -fPIC "-I/usr/lib/perl/5.8/CORE"  -DHAVE_JPEG -DHAVE_FT -DHAVE_XPM -DHAVE_GIF -DHAVE_PNG -DHAVE_ANIMGIF GD.c
GD.xs:7:16: error: gd.h: No such file or directory
GD.xs:8:21: error: gdfontg.h: No such file or directory
GD.xs:9:21: error: gdfontl.h: No such file or directory
GD.xs:10:22: error: gdfontmb.h: No such file or directory
GD.xs:11:21: error: gdfonts.h: No such file or directory
GD.xs:12:21: error: gdfontt.h: No such file or directory
GD.xs:336: error: syntax error before 'GD__Image'
GD.xs:336: warning: data definition has no type or storage class
GD.xs:337: error: syntax error before 'GD__Font'
GD.xs:337: warning: data definition has no type or storage class
GD.xs:379: error: syntax error before 'gdIOCtx'
GD.xs:379: warning: no semicolon at end of struct or union
GD.xs:383: error: syntax error before '}' token
GD.xs:383: warning: data definition has no type or storage class
GD.xs:387: error: syntax error before 'ctx'
GD.xs: In function 'bufGetC':
GD.xs:388: error: 'ctx' undeclared (first use in this function)
GD.xs:388: error: (Each undeclared identifier is reported only once
GD.xs:388: error: for each function it appears in.)
GD.xs:390: error: dereferencing pointer to incomplete type
GD.xs:390: error: dereferencing pointer to incomplete type
GD.xs:391: error: dereferencing pointer to incomplete type
GD.xs:391: error: dereferencing pointer to incomplete type
GD.xs: At top level:
GD.xs:394: error: syntax error before 'ctx'
GD.xs: In function 'bufGetBuf':
GD.xs:395: error: 'ctx' undeclared (first use in this function)
GD.xs:398: error: dereferencing pointer to incomplete type
GD.xs:398: error: dereferencing pointer to incomplete type
GD.xs:399: error: 'len' undeclared (first use in this function)
GD.xs:405: error: 'buf' undeclared (first use in this function)
GD.xs:405: error: dereferencing pointer to incomplete type
GD.xs:405: error: dereferencing pointer to incomplete type
GD.xs:406: error: dereferencing pointer to incomplete type
GD.xs: At top level:
GD.xs:410: error: syntax error before 'ctx'
GD.xs: In function 'bufSeek':
GD.xs:411: error: 'ctx' undeclared (first use in this function)
GD.xs:412: error: dereferencing pointer to incomplete type
GD.xs:413: error: dereferencing pointer to incomplete type
GD.xs:413: error: dereferencing pointer to incomplete type
GD.xs:414: error: dereferencing pointer to incomplete type
GD.xs:414: error: dereferencing pointer to incomplete type
GD.xs: At top level:
GD.xs:418: error: syntax error before 'ctx'
GD.xs: In function 'bufTell':
GD.xs:419: error: 'ctx' undeclared (first use in this function)
GD.xs:420: error: dereferencing pointer to incomplete type
GD.xs: At top level:
GD.xs:423: error: syntax error before 'ctx'
GD.xs: In function 'bufFree':
GD.xs:424: error: 'ctx' undeclared (first use in this function)
GD.xs: At top level:
GD.xs:427: error: syntax error before '*' token
GD.xs: In function 'newDynamicCtx':
GD.xs:430: error: syntax error before ')' token
GD.xs:430: error: syntax error before ')' token
GD.xs:432: error: dereferencing pointer to incomplete type
GD.xs:433: error: dereferencing pointer to incomplete type
GD.xs:434: error: dereferencing pointer to incomplete type
GD.xs:436: error: dereferencing pointer to incomplete type
GD.xs:437: error: dereferencing pointer to incomplete type
GD.xs:438: error: dereferencing pointer to incomplete type
GD.xs:439: error: dereferencing pointer to incomplete type
GD.xs:440: error: dereferencing pointer to incomplete type
GD.xs:441: error: dereferencing pointer to incomplete type
GD.xs:442: error: dereferencing pointer to incomplete type
GD.xs:443: error: 'gdIOCtx' undeclared (first use in this function)
GD.xs:443: error: syntax error before ')' token
GD.xs: At top level:
GD.xs:448: error: syntax error before 'gd_cloneDim'
GD.xs:448: error: syntax error before 'src'
GD.xs: In function 'gd_cloneDim':
GD.xs:449: error: syntax error before 'dst'
GD.xs:450: error: 'src' undeclared (first use in this function)
GD.xs:451: error: 'dst' undeclared (first use in this function)
GD.xs:451: error: syntax error before 'gdImageCreateTrueColor'
GD.xs:454: error: syntax error before 'gdImageCreatePalette'
GD.xs:456: error: 'gdMaxColors' undeclared (first use in this function)
GD.xs: At top level:
GD.xs:472: error: syntax error before 'src'
GD.xs: In function 'get_xformbounds':
GD.xs:475: error: 'x' undeclared (first use in this function)
GD.xs:475: error: 'src' undeclared (first use in this function)
GD.xs:476: error: 'y' undeclared (first use in this function)
GD.xs:477: error: 'x1' undeclared (first use in this function)
GD.xs:479: error: 'x2' undeclared (first use in this function)
GD.xs:480: error: 'y2' undeclared (first use in this function)
GD.xs: At top level:
GD.xs:501: error: syntax error before 'image'
GD.xs: In function 'gd_chkimagefmt':
GD.xs:502: error: 'image' undeclared (first use in this function)
GD.xs:503: error: 'truecolor' undeclared (first use in this function)
GD.xs:505: error: 'gdMaxColors' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image__new':
GD.c:593: error: syntax error before 'RETVAL'
GD.xs:568: error: 'gdImagePtr' undeclared (first use in this function)
GD.xs:568: error: syntax error before 'theImage'
GD.xs:572: error: 'theImage' undeclared (first use in this function)
GD.xs:572: error: syntax error before 'gdImageCreateTrueColor'
GD.xs:574: error: syntax error before 'gdImageCreate'
GD.xs:576: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image__newFromPng':
GD.c:647: error: syntax error before 'RETVAL'
GD.xs:591: error: 'RETVAL' undeclared (first use in this function)
GD.xs:591: error: syntax error before 'gdImageCreateFromPng'
GD.xs: In function 'XS_GD__Image_newFromPngData':
GD.xs:604: error: 'gdIOCtx' undeclared (first use in this function)
GD.xs:604: error: 'ctx' undeclared (first use in this function)
GD.c:681: error: syntax error before 'RETVAL'
GD.xs:611: error: 'RETVAL' undeclared (first use in this function)
GD.xs:611: error: syntax error before 'gdImageCreateFromPngCtx'
GD.c: In function 'XS_GD__Image_newFromGdData':
GD.c:716: error: syntax error before 'RETVAL'
GD.xs:630: error: 'RETVAL' undeclared (first use in this function)
GD.xs:630: error: syntax error before 'gdImageCreateFromGdPtr'
GD.c: In function 'XS_GD__Image_newFromGd2Data':
GD.c:746: error: syntax error before 'RETVAL'
GD.xs:644: error: 'RETVAL' undeclared (first use in this function)
GD.xs:644: error: syntax error before 'gdImageCreateFromGd2Ptr'
GD.xs: In function 'XS_GD__Image_newFromJpegData':
GD.xs:656: error: 'gdIOCtx' undeclared (first use in this function)
GD.xs:656: error: 'ctx' undeclared (first use in this function)
GD.c:782: error: syntax error before 'RETVAL'
GD.xs:663: error: 'RETVAL' undeclared (first use in this function)
GD.xs:663: error: syntax error before 'gdImageCreateFromJpegCtx'
GD.xs: In function 'XS_GD__Image_newFromWBMPData':
GD.xs:679: error: 'gdIOCtx' undeclared (first use in this function)
GD.xs:679: error: 'ctx' undeclared (first use in this function)
GD.c:820: error: syntax error before 'RETVAL'
GD.xs:686: error: 'RETVAL' undeclared (first use in this function)
GD.xs:686: error: syntax error before 'gdImageCreateFromWBMPCtx'
GD.c: In function 'XS_GD__Image__newFromXbm':
GD.c:850: error: syntax error before 'RETVAL'
GD.xs:699: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image__newFromGd':
GD.c:875: error: syntax error before 'RETVAL'
GD.xs:709: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image__newFromGd2':
GD.c:900: error: syntax error before 'RETVAL'
GD.xs:719: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image__newFromJpeg':
GD.c:932: error: syntax error before 'RETVAL'
GD.xs:733: error: 'RETVAL' undeclared (first use in this function)
GD.xs: In function 'XS_GD__Image__newFromWBMP':
GD.xs:747: error: 'gdImagePtr' undeclared (first use in this function)
GD.xs:747: error: syntax error before 'img'
GD.c:964: error: syntax error before 'RETVAL'
GD.xs:750: error: 'img' undeclared (first use in this function)
GD.xs:757: error: 'RETVAL' undeclared (first use in this function)
GD.xs: In function 'XS_GD__Image_newFromXpm':
GD.xs:767: error: 'gdImagePtr' undeclared (first use in this function)
GD.xs:767: error: syntax error before 'img'
GD.c:1000: error: syntax error before 'RETVAL'
GD.xs:771: error: 'img' undeclared (first use in this function)
GD.xs:771: error: syntax error before 'gdImageCreateFromXpm'
GD.xs:778: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image__newFromGd2Part':
GD.c:1042: error: syntax error before 'RETVAL'
GD.xs:797: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image__newFromGif':
GD.c:1074: error: syntax error before 'RETVAL'
GD.xs:811: error: 'RETVAL' undeclared (first use in this function)
GD.xs: In function 'XS_GD__Image_newFromGifData':
GD.xs:822: error: 'gdIOCtx' undeclared (first use in this function)
GD.xs:822: error: 'ctx' undeclared (first use in this function)
GD.c:1106: error: syntax error before 'RETVAL'
GD.xs:829: error: 'RETVAL' undeclared (first use in this function)
GD.xs:829: error: syntax error before 'gdImageCreateFromGifCtx'
GD.c: In function 'XS_GD__Image_DESTROY':
GD.c:1133: error: syntax error before 'image'
GD.c:1137: error: 'image' undeclared (first use in this function)
GD.c:1137: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_png':
GD.c:1160: error: syntax error before 'image'
GD.c:1167: error: 'image' undeclared (first use in this function)
GD.c:1167: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_jpeg':
GD.c:1203: error: syntax error before 'image'
GD.c:1212: error: 'image' undeclared (first use in this function)
GD.c:1212: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_gifanimbegin':
GD.c:1251: error: syntax error before 'image'
GD.c:1260: error: 'image' undeclared (first use in this function)
GD.c:1260: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_gifanimadd':
GD.c:1302: error: syntax error before 'image'
GD.c:1308: error: syntax error before 'previm'
GD.c:1313: error: 'image' undeclared (first use in this function)
GD.c:1313: error: called object 'GD__Image' is not a function
GD.c:1349: error: 'previm' undeclared (first use in this function)
GD.c:1353: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_gifanimend':
GD.c:1384: error: syntax error before 'image'
GD.c:1389: error: 'image' undeclared (first use in this function)
GD.c:1389: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_wbmp':
GD.c:1419: error: syntax error before 'image'
GD.c:1428: error: 'image' undeclared (first use in this function)
GD.c:1428: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_gif':
GD.c:1463: error: syntax error before 'image'
GD.c:1471: error: 'image' undeclared (first use in this function)
GD.c:1471: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_gd':
GD.c:1504: error: syntax error before 'image'
GD.c:1509: error: 'image' undeclared (first use in this function)
GD.c:1509: error: called object 'GD__Image' is not a function
GD.xs:1021: warning: assignment makes pointer from integer without a cast
GD.c: In function 'XS_GD__Image_gd2':
GD.c:1535: error: syntax error before 'image'
GD.c:1540: error: 'image' undeclared (first use in this function)
GD.c:1540: error: called object 'GD__Image' is not a function
GD.xs:1036: error: 'GD2_FMT_COMPRESSED' undeclared (first use in this function)
GD.xs:1036: warning: assignment makes pointer from integer without a cast
GD.c: In function 'XS_GD__Image_transparent':
GD.c:1566: error: syntax error before 'image'
GD.c:1572: error: 'image' undeclared (first use in this function)
GD.c:1572: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_getBounds':
GD.c:1599: error: syntax error before 'image'
GD.c:1603: error: 'image' undeclared (first use in this function)
GD.c:1603: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_isTrueColor':
GD.c:1629: error: syntax error before 'image'
GD.c:1635: error: 'image' undeclared (first use in this function)
GD.c:1635: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_trueColorToPalette':
GD.c:1656: error: syntax error before 'image'
GD.c:1662: error: 'image' undeclared (first use in this function)
GD.c:1662: error: called object 'GD__Image' is not a function
GD.c:1674: error: 'gdMaxColors' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image_rgb':
GD.c:1695: error: syntax error before 'image'
GD.c:1700: error: 'image' undeclared (first use in this function)
GD.c:1700: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_boundsSafe':
GD.c:1728: error: syntax error before 'image'
GD.c:1736: error: 'image' undeclared (first use in this function)
GD.c:1736: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_getPixel':
GD.c:1759: error: syntax error before 'image'
GD.c:1767: error: 'image' undeclared (first use in this function)
GD.c:1767: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_setPixel':
GD.c:1788: error: syntax error before 'image'
GD.c:1795: error: 'image' undeclared (first use in this function)
GD.c:1795: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_copyRotate90':
GD.c:1815: error: syntax error before 'src'
GD.c:1820: error: 'src' undeclared (first use in this function)
GD.c:1820: error: called object 'GD__Image' is not a function
GD.xs:1159: error: syntax error before 'dst'
GD.xs:1161: error: 'dst' undeclared (first use in this function)
GD.xs:1161: error: syntax error before 'gd_cloneDim'
GD.xs:1165: error: invalid lvalue in assignment
GD.xs:1165: error: invalid lvalue in assignment
GD.xs:1168: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image_copyRotate180':
GD.c:1852: error: syntax error before 'src'
GD.c:1857: error: 'src' undeclared (first use in this function)
GD.c:1857: error: called object 'GD__Image' is not a function
GD.xs:1180: error: syntax error before 'dst'
GD.xs:1182: error: 'dst' undeclared (first use in this function)
GD.xs:1182: error: syntax error before 'gd_cloneDim'
GD.xs:1186: error: invalid lvalue in assignment
GD.xs:1186: error: invalid lvalue in assignment
GD.xs:1189: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image_copyRotate270':
GD.c:1889: error: syntax error before 'src'
GD.c:1894: error: 'src' undeclared (first use in this function)
GD.c:1894: error: called object 'GD__Image' is not a function
GD.xs:1201: error: syntax error before 'dst'
GD.xs:1203: error: 'dst' undeclared (first use in this function)
GD.xs:1203: error: syntax error before 'gd_cloneDim'
GD.xs:1207: error: invalid lvalue in assignment
GD.xs:1207: error: invalid lvalue in assignment
GD.xs:1210: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image_copyFlipHorizontal':
GD.c:1926: error: syntax error before 'src'
GD.c:1931: error: 'src' undeclared (first use in this function)
GD.c:1931: error: called object 'GD__Image' is not a function
GD.xs:1222: error: syntax error before 'dst'
GD.xs:1224: error: 'dst' undeclared (first use in this function)
GD.xs:1224: error: syntax error before 'gd_cloneDim'
GD.xs:1228: error: invalid lvalue in assignment
GD.xs:1228: error: invalid lvalue in assignment
GD.xs:1231: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image_copyFlipVertical':
GD.c:1963: error: syntax error before 'src'
GD.c:1968: error: 'src' undeclared (first use in this function)
GD.c:1968: error: called object 'GD__Image' is not a function
GD.xs:1243: error: syntax error before 'dst'
GD.xs:1245: error: 'dst' undeclared (first use in this function)
GD.xs:1245: error: syntax error before 'gd_cloneDim'
GD.xs:1249: error: invalid lvalue in assignment
GD.xs:1249: error: invalid lvalue in assignment
GD.xs:1252: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image_copyTranspose':
GD.c:2000: error: syntax error before 'src'
GD.c:2005: error: 'src' undeclared (first use in this function)
GD.c:2005: error: called object 'GD__Image' is not a function
GD.xs:1264: error: syntax error before 'dst'
GD.xs:1266: error: 'dst' undeclared (first use in this function)
GD.xs:1266: error: syntax error before 'gd_cloneDim'
GD.xs:1270: error: invalid lvalue in assignment
GD.xs:1270: error: invalid lvalue in assignment
GD.xs:1273: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image_copyReverseTranspose':
GD.c:2037: error: syntax error before 'src'
GD.c:2042: error: 'src' undeclared (first use in this function)
GD.c:2042: error: called object 'GD__Image' is not a function
GD.xs:1285: error: syntax error before 'dst'
GD.xs:1287: error: 'dst' undeclared (first use in this function)
GD.xs:1287: error: syntax error before 'gd_cloneDim'
GD.xs:1291: error: invalid lvalue in assignment
GD.xs:1291: error: invalid lvalue in assignment
GD.xs:1294: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Image_rotate180':
GD.c:2074: error: syntax error before 'src'
GD.c:2078: error: 'src' undeclared (first use in this function)
GD.c:2078: error: called object 'GD__Image' is not a function
GD.xs:1311: error: invalid lvalue in assignment
GD.xs:1311: error: invalid lvalue in assignment
GD.xs:1312: error: invalid lvalue in assignment
GD.xs:1312: error: invalid lvalue in assignment
GD.c: In function 'XS_GD__Image_copyRotated':
GD.c:2107: error: syntax error before 'dst'
GD.c:2119: error: 'dst' undeclared (first use in this function)
GD.c:2119: error: called object 'GD__Image' is not a function
GD.c:2126: error: 'src' undeclared (first use in this function)
GD.c:2126: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_flipHorizontal':
GD.c:2150: error: syntax error before 'src'
GD.c:2154: error: 'src' undeclared (first use in this function)
GD.c:2154: error: called object 'GD__Image' is not a function
GD.xs:1350: error: invalid lvalue in assignment
GD.xs:1350: error: invalid lvalue in assignment
GD.xs:1351: error: invalid lvalue in assignment
GD.xs:1351: error: invalid lvalue in assignment
GD.c: In function 'XS_GD__Image_flipVertical':
GD.c:2183: error: syntax error before 'src'
GD.c:2187: error: 'src' undeclared (first use in this function)
GD.c:2187: error: called object 'GD__Image' is not a function
GD.xs:1368: error: invalid lvalue in assignment
GD.xs:1368: error: invalid lvalue in assignment
GD.xs:1369: error: invalid lvalue in assignment
GD.xs:1369: error: invalid lvalue in assignment
GD.c: In function 'XS_GD__Image_line':
GD.c:2216: error: syntax error before 'image'
GD.c:2225: error: 'image' undeclared (first use in this function)
GD.c:2225: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_dashedLine':
GD.c:2245: error: syntax error before 'image'
GD.c:2254: error: 'image' undeclared (first use in this function)
GD.c:2254: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_openPolygon':
GD.c:2274: error: syntax error before 'image'
GD.c:2280: error: 'image' undeclared (first use in this function)
GD.c:2280: error: called object 'GD__Image' is not a function
GD.xs:1413: error: 'gdPointPtr' undeclared (first use in this function)
GD.xs:1413: error: syntax error before 'polyptr'
GD.xs:1429: error: 'polyptr' undeclared (first use in this function)
GD.xs:1429: error: syntax error before 'Perl_safesysmalloc'
GD.c: In function 'XS_GD__Image_unclosedPolygon':
GD.c:2345: error: syntax error before 'image'
GD.c:2351: error: 'image' undeclared (first use in this function)
GD.c:2351: error: called object 'GD__Image' is not a function
GD.xs:1469: error: 'gdPointPtr' undeclared (first use in this function)
GD.xs:1469: error: syntax error before 'polyptr'
GD.c: In function 'XS_GD__Image_filledPolygon':
GD.c:2419: error: syntax error before 'image'

```

rest of code block in next post.

---

### Post by dbunder on 2006-04-22
```



GD.c:2425: error: 'image' undeclared (first use in this function)
GD.c:2425: error: called object 'GD__Image' is not a function
GD.xs:1528: error: 'gdPointPtr' undeclared (first use in this function)
GD.xs:1528: error: syntax error before 'polyptr'
GD.xs:1544: error: 'polyptr' undeclared (first use in this function)
GD.xs:1544: error: syntax error before 'Perl_safesysmalloc'
GD.c: In function 'XS_GD__Image_rectangle':
GD.c:2490: error: syntax error before 'image'
GD.c:2499: error: 'image' undeclared (first use in this function)
GD.c:2499: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_filledRectangle':
GD.c:2519: error: syntax error before 'image'
GD.c:2528: error: 'image' undeclared (first use in this function)
GD.c:2528: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_filledEllipse':
GD.c:2548: error: syntax error before 'image'
GD.c:2557: error: 'image' undeclared (first use in this function)
GD.c:2557: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_arc':
GD.c:2577: error: syntax error before 'image'
GD.c:2588: error: 'image' undeclared (first use in this function)
GD.c:2588: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_filledArc':
GD.c:2608: error: syntax error before 'image'
GD.c:2620: error: 'image' undeclared (first use in this function)
GD.c:2620: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_fillToBorder':
GD.c:2646: error: syntax error before 'image'
GD.c:2654: error: 'image' undeclared (first use in this function)
GD.c:2654: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_fill':
GD.c:2674: error: syntax error before 'image'
GD.c:2681: error: 'image' undeclared (first use in this function)
GD.c:2681: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_setBrush':
GD.c:2701: error: syntax error before 'image'
GD.c:2706: error: 'image' undeclared (first use in this function)
GD.c:2706: error: called object 'GD__Image' is not a function
GD.c:2713: error: 'brush' undeclared (first use in this function)
GD.c:2713: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_setTile':
GD.c:2733: error: syntax error before 'image'
GD.c:2738: error: 'image' undeclared (first use in this function)
GD.c:2738: error: called object 'GD__Image' is not a function
GD.c:2745: error: 'tile' undeclared (first use in this function)
GD.c:2745: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_setThickness':
GD.c:2765: error: syntax error before 'image'
GD.c:2770: error: 'image' undeclared (first use in this function)
GD.c:2770: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_setStyle':
GD.c:2790: error: syntax error before 'image'
GD.c:2794: error: 'image' undeclared (first use in this function)
GD.c:2794: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorAllocate':
GD.c:2826: error: syntax error before 'image'
GD.c:2835: error: 'image' undeclared (first use in this function)
GD.c:2835: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorAllocateAlpha':
GD.c:2856: error: syntax error before 'image'
GD.c:2866: error: 'image' undeclared (first use in this function)
GD.c:2866: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorClosest':
GD.c:2887: error: syntax error before 'image'
GD.c:2896: error: 'image' undeclared (first use in this function)
GD.c:2896: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorClosestAlpha':
GD.c:2917: error: syntax error before 'image'
GD.c:2927: error: 'image' undeclared (first use in this function)
GD.c:2927: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorClosestHWB':
GD.c:2948: error: syntax error before 'image'
GD.c:2957: error: 'image' undeclared (first use in this function)
GD.c:2957: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorExact':
GD.c:2978: error: syntax error before 'image'
GD.c:2987: error: 'image' undeclared (first use in this function)
GD.c:2987: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorExactAlpha':
GD.c:3008: error: syntax error before 'image'
GD.c:3018: error: 'image' undeclared (first use in this function)
GD.c:3018: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorResolve':
GD.c:3039: error: syntax error before 'image'
GD.c:3048: error: 'image' undeclared (first use in this function)
GD.c:3048: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorResolveAlpha':
GD.c:3069: error: syntax error before 'image'
GD.c:3079: error: 'image' undeclared (first use in this function)
GD.c:3079: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorsTotal':
GD.c:3100: error: syntax error before 'image'
GD.c:3106: error: 'image' undeclared (first use in this function)
GD.c:3106: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_interlaced':
GD.c:3129: error: syntax error before 'image'
GD.c:3135: error: 'image' undeclared (first use in this function)
GD.c:3135: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_compare':
GD.c:3162: error: syntax error before 'image1'
GD.c:3169: error: 'image1' undeclared (first use in this function)
GD.c:3169: error: called object 'GD__Image' is not a function
GD.c:3176: error: 'image2' undeclared (first use in this function)
GD.c:3176: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_colorDeallocate':
GD.c:3197: error: syntax error before 'image'
GD.c:3202: error: 'image' undeclared (first use in this function)
GD.c:3202: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_copy':
GD.c:3222: error: syntax error before 'destination'
GD.c:3233: error: 'destination' undeclared (first use in this function)
GD.c:3233: error: called object 'GD__Image' is not a function
GD.c:3240: error: 'source' undeclared (first use in this function)
GD.c:3240: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_copyResized':
GD.c:3260: error: syntax error before 'destination'
GD.c:3273: error: 'destination' undeclared (first use in this function)
GD.c:3273: error: called object 'GD__Image' is not a function
GD.c:3280: error: 'source' undeclared (first use in this function)
GD.c:3280: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_copyResampled':
GD.c:3300: error: syntax error before 'destination'
GD.c:3313: error: 'destination' undeclared (first use in this function)
GD.c:3313: error: called object 'GD__Image' is not a function
GD.c:3320: error: 'source' undeclared (first use in this function)
GD.c:3320: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_copyMerge':
GD.c:3340: error: syntax error before 'destination'
GD.c:3352: error: 'destination' undeclared (first use in this function)
GD.c:3352: error: called object 'GD__Image' is not a function
GD.c:3359: error: 'source' undeclared (first use in this function)
GD.c:3359: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_copyMergeGray':
GD.c:3379: error: syntax error before 'destination'
GD.c:3391: error: 'destination' undeclared (first use in this function)
GD.c:3391: error: called object 'GD__Image' is not a function
GD.c:3398: error: 'source' undeclared (first use in this function)
GD.c:3398: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_paletteCopy':
GD.c:3418: error: syntax error before 'destination'
GD.c:3423: error: 'destination' undeclared (first use in this function)
GD.c:3423: error: called object 'GD__Image' is not a function
GD.c:3430: error: 'source' undeclared (first use in this function)
GD.c:3430: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_char':
GD.c:3450: error: syntax error before 'image'
GD.c:3459: error: 'image' undeclared (first use in this function)
GD.c:3459: error: called object 'GD__Image' is not a function
GD.c:3466: error: 'font' undeclared (first use in this function)
GD.c:3466: error: called object 'GD__Font' is not a function
GD.c: In function 'XS_GD__Image_charUp':
GD.c:3486: error: syntax error before 'image'
GD.c:3495: error: 'image' undeclared (first use in this function)
GD.c:3495: error: called object 'GD__Image' is not a function
GD.c:3502: error: 'font' undeclared (first use in this function)
GD.c:3502: error: called object 'GD__Font' is not a function
GD.c: In function 'XS_GD__Image_string':
GD.c:3522: error: syntax error before 'image'
GD.c:3531: error: 'image' undeclared (first use in this function)
GD.c:3531: error: called object 'GD__Image' is not a function
GD.c:3538: error: 'font' undeclared (first use in this function)
GD.c:3538: error: called object 'GD__Font' is not a function
GD.c: In function 'XS_GD__Image_stringUp':
GD.c:3558: error: syntax error before 'image'
GD.c:3567: error: 'image' undeclared (first use in this function)
GD.c:3567: error: called object 'GD__Image' is not a function
GD.c:3574: error: 'font' undeclared (first use in this function)
GD.c:3574: error: called object 'GD__Font' is not a function
GD.xs: In function 'XS_GD__Image_stringFT':
GD.xs:2072: error: 'gdImagePtr' undeclared (first use in this function)
GD.xs:2072: error: syntax error before 'img'
GD.xs:2082: error: 'gdFTStringExtra' undeclared (first use in this function)
GD.xs:2082: error: syntax error before 'strex'
GD.xs:2092: error: 'img' undeclared (first use in this function)
GD.xs:2092: error: syntax error before 'tmp'
GD.xs:2101: error: 'strex' undeclared (first use in this function)
GD.xs:2105: error: 'gdFTEX_LINESPACE' undeclared (first use in this function)
GD.xs:2109: error: 'gdFTEX_CHARMAP' undeclared (first use in this function)
GD.xs:2111: error: 'gdFTEX_Unicode' undeclared (first use in this function)
GD.xs:2113: error: 'gdFTEX_Shift_JIS' undeclared (first use in this function)
GD.xs:2115: error: 'gdFTEX_Big5' undeclared (first use in this function)
GD.xs:2136: warning: assignment makes pointer from integer without a cast
GD.xs:2140: warning: assignment makes pointer from integer without a cast
GD.c: In function 'XS_GD__Image_stringFTCircle':
GD.c:3701: error: syntax error before 'image'
GD.c:3721: error: 'image' undeclared (first use in this function)
GD.c:3721: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_useFontConfig':
GD.c:3766: error: syntax error before 'image'
GD.c:3776: error: 'image' undeclared (first use in this function)
GD.c:3776: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_alphaBlending':
GD.c:3803: error: syntax error before 'image'
GD.c:3808: error: 'image' undeclared (first use in this function)
GD.c:3808: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_saveAlpha':
GD.c:3828: error: syntax error before 'image'
GD.c:3833: error: 'image' undeclared (first use in this function)
GD.c:3833: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_clip':
GD.c:3854: error: syntax error before 'image'
GD.c:3862: error: 'image' undeclared (first use in this function)
GD.c:3862: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_setAntiAliased':
GD.c:3894: error: syntax error before 'image'
GD.c:3899: error: 'image' undeclared (first use in this function)
GD.c:3899: error: called object 'GD__Image' is not a function
GD.c: In function 'XS_GD__Image_setAntiAliasedDontBlend':
GD.c:3919: error: syntax error before 'image'
GD.c:3925: error: 'image' undeclared (first use in this function)
GD.c:3925: error: called object 'GD__Image' is not a function
GD.xs: In function 'XS_GD__Font_load':
GD.xs:2302: error: 'gdFontPtr' undeclared (first use in this function)
GD.xs:2302: error: syntax error before 'font'
GD.c:3962: error: syntax error before 'RETVAL'
GD.xs:2314: error: 'font' undeclared (first use in this function)
GD.xs:2314: error: syntax error before 'Perl_safesysmalloc'
GD.xs:2345: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Font_DESTROY':
GD.c:4025: error: syntax error before 'self'
GD.c:4029: error: 'self' undeclared (first use in this function)
GD.c:4029: error: called object 'GD__Font' is not a function
GD.c: In function 'XS_GD__Font_Small':
GD.c:4057: error: syntax error before 'RETVAL'
GD.xs:2372: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Font_Large':
GD.c:4083: error: syntax error before 'RETVAL'
GD.xs:2383: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Font_Giant':
GD.c:4109: error: syntax error before 'RETVAL'
GD.xs:2394: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Font_MediumBold':
GD.c:4135: error: syntax error before 'RETVAL'
GD.xs:2405: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Font_Tiny':
GD.c:4161: error: syntax error before 'RETVAL'
GD.xs:2416: error: 'RETVAL' undeclared (first use in this function)
GD.c: In function 'XS_GD__Font_nchars':
GD.c:4186: error: syntax error before 'font'
GD.c:4192: error: 'font' undeclared (first use in this function)
GD.c:4192: error: called object 'GD__Font' is not a function
GD.c: In function 'XS_GD__Font_offset':
GD.c:4213: error: syntax error before 'font'
GD.c:4219: error: 'font' undeclared (first use in this function)
GD.c:4219: error: called object 'GD__Font' is not a function
GD.c: In function 'XS_GD__Font_width':
GD.c:4240: error: syntax error before 'font'
GD.c:4246: error: 'font' undeclared (first use in this function)
GD.c:4246: error: called object 'GD__Font' is not a function
GD.c: In function 'XS_GD__Font_height':
GD.c:4267: error: syntax error before 'font'
GD.c:4273: error: 'font' undeclared (first use in this function)
GD.c:4273: error: called object 'GD__Font' is not a function
make: *** [GD.o] Error 1
  /usr/bin/make  -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible
Failed during this command:
  LDS/GD-2.32.tar.gz                           : make NO

```

Thanks for any insight into this.  It's craaaazy-makin'.

edit: Oh, and I understand I can simply install the GD perl module with synaptic or apt-get, but for such things that require performance, I like to compile them myself with my own optimizations for the box I'll be running it from.

---

### Post by dharry on 2006-05-14
Perl GD-2.32 currently fails during build (make) with following errors:

/usr/bin/perl -I/usr/opt/perl5/lib/5.6.0/aix -I/usr/opt/perl5/lib/5.6.0 /usr/opt
/perl5/lib/5.6.0/ExtUtils/xsubpp  -typemap /usr/opt/perl5/lib/5.6.0/ExtUtils/typ
emap -typemap typemap GD.xs > GD.xsc && mv GD.xsc GD.c
cc -c -I/usr/include -D_ALL_SOURCE -D_ANSI_C_SOURCE -D_POSIX_SOURCE -qmaxmem=163
84 -q32 -D_LARGE_FILES -qlonglong -O     -DVERSION=\"2.32\" -DXS_VERSION=\"2.32\
"  -I/usr/opt/perl5/lib/5.6.0/aix/CORE -DHAVE_JPEG -DHAVE_FT -DHAVE_PNG GD.c
"GD.c", line 534.1: 1506-277 (S) Syntax error: possible missing ';' or ','?
"GD.c", line 535.5: 1506-277 (S) Syntax error: possible missing ';' or ','?
"GD.c", line 535.5: 1506-277 (S) Syntax error: possible missing ';' or ','?
"GD.xs", line 521.1: 1506-485 (S) Parameter declaration list is incompatible wit
h declarator for START_MY_CXT.
"GD.c", line 539.37: 1506-045 (S) Undeclared identifier ax.
"GD.c", line 544.9: 1506-045 (S) Undeclared identifier sp.
"GD.c", line 546.5: 1506-046 (S) Syntax error.
make: *** [GD.o] Error 1

Could somebody please help? 

Thanks.

---

### Post by w9wi on 2007-07-02
Well, this is probably way too late to do the OP any good(grin) but maybe it'll help the next person who finds this thread...

I was having the exact same problem.  Turns out you must install the *developer* version of lib-gd.  The one with -dev on the end of the package name -- in my case libgd2-xpm-dev.  

Working fine now...

---

### Post by rwales on 2007-08-08
I'll second w9wi's post. I had exactly the same problem as the OP on feisty. I ran

```
sudo apt-get install libgd2-xpm-dev
```

then the following command worked fine (didn't even ask for the libgd location).

```
sudo perl -MCPAN -e 'install GD'
```

---

### Post by alexsavencu on 2008-06-12
greetings,

although I have the libgd2-xpm-dev installed, at the end of the GD module installation I have the messages specified below... I can't figure out what the problem is, so please provide help

Removing previously used /home/alexandru/.cpan/build/GD-2.39

  CPAN.pm: Going to build L/LD/LDS/GD-2.39.tar.gz

Configuring for libgd version 2.0.35.
Checking for stray libgd header files...none found.

Included Features:          GD_XPM GD_JPEG GD_FONTCONFIG GD_FREETYPE GD_PNG GD_GIF GD_GIFANIM GD_OPENPOLYGON GD_UNCLOSEDPOLY GD_ANIMGIF GD_FTCIRCLE VERSION_33
GD library used from:       /usr
Checking if your kit is complete...
Looks good
Writing Makefile for GD
    -- NOT OK
Running make test
  Can't test without successful make
Running make install
  make had returned bad status, install seems impossible

---

