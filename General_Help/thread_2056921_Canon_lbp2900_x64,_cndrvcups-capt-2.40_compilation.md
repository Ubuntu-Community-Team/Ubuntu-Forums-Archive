---
title: "Canon lbp2900 x64, cndrvcups-capt-2.40 compilation failure"
date: 2012-09-12
forum: General Help
---

### Post by deff182 on 2012-09-12
I'm following the [*official tutorial*]("https://help.ubuntu.com/community/CanonCaptDrv190") on installing Canon LBP2900 drivers. Since there're no ready-made packages for x64 platform I have to compile...

cndrvcups-common-2.40 has been compiled and installed - at least I haven't seen any errors. The second one, cndrvcups-capt-2.40, _doesn't contain Makefile_ in it but README also says that ./allgen.sh option available which leads me to:


```
checking for ANSI C header files... (cached) yes
./configure: line 13072: syntax error near unexpected token `1.2.0,'
./configure: line 13072: `AM_PATH_GTK(1.2.0, ,'
/home/midnight/Downloads/Linux_CAPT_PrinterDriver_V240_uk_EN/Src/cndrvcups-capt-2.40
for dir in driver backend pstocapt pstocapt2 pstocapt3 statusui ppd cngplp; do\
		echo Making modules $dir ...;\
		(cd $dir; make) || exit 1;\
	done
```

with later:
```
make[1]: Entering directory `/home/midnight/Downloads/Linux_CAPT_PrinterDriver_V240_uk_EN/Src/cndrvcups-capt-2.40/statusui'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/midnight/Downloads/Linux_CAPT_PrinterDriver_V240_uk_EN/Src/cndrvcups-capt-2.40/statusui'
```


The thing is statusui couldn't be compiled because of 

```
./configure: line 13072: syntax error near unexpected token `1.2.0,'
./configure: line 13072: `AM_PATH_GTK(1.2.0, ,'
```

Does Anyone know how to fix it ?

P.S. AM_PATH_GTK(1.2.0 imho is related to gtk1.2 however I have gtk2.0 + dev isntalled.

UPD

if it's really libgtk1.2 then how to justify [[COLOR="Navy"]_this_[/COLOR]]("http://imgur.com/nHLEP") ? GIMP ? 
[IMG]http://imgur.com/nHLEP[/IMG]

**UPD2**

Nevermind what I've written in above. Eventually I got alien and converted x64 rpms, though it's sad that I still had to do it. I still have problems :-D which I'll post in another thread.

---

### Post by tonidito on 2012-11-12
Hi,
if You want to compile the drivers and create deb packages, please follow instructions at the following web page:

[http://ubuntuforums.org/showthread.p...5#post12350075]("http://ubuntuforums.org/showthread.php?p=12350075#post12350075")
(#12)

and You will solve the problem with Canon CAPT printer drivers!

tonidito:razz:

---

