---
title: "linuxant drivers will no longer install"
date: 2011-04-30
forum: General Help
---

### Post by 98174 on 2011-04-30
I am trying to install the Linuxant ALSA driver on 11.04 from [http://www.linuxant.com/alsa-driver/]("http://www.linuxant.com/alsa-driver/")

From the error log:
```

287 /usr/lib/alsa-driver-linuxant/acore/pcm_native.c: In function &#8216;snd_pcm_hw_params&#8217;:
288 /usr/lib/alsa-driver-linuxant/acore/pcm_native.c:489:2: error: implicit declaration of function &#8216;pm_qos_remove_requirement&#8217;
289 /usr/lib/alsa-driver-linuxant/acore/pcm_native.c:492:3: error: implicit declaration of function &#8216;pm_qos_add_requirement&#8217;
290 make[3]: *** [/usr/lib/alsa-driver-linuxant/acore/pcm_native.o] Error 1
291 make[2]: *** [/usr/lib/alsa-driver-linuxant/acore] Error 2
292 make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
293 make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
294 make: *** [compile] Error 2

```

This worked fine on Ubuntu 10.04 (didn't try 10.10).  Any way to work around this?  Not having sound means Natty is kind of useless =/

---

### Post by 98174 on 2011-04-30
Any ideas?

---

### Post by 98174 on 2011-05-16
Bumpty-Bump.

---

### Post by anderedna on 2011-07-12
Hi,   I'm getting the same problem as well. Im on 11.04 with kernel 2.6.38-10-generic.  Getting the build problem from the log file and now while trying to install modem from linmodems. Now the sound and modem both are not working.  Any idea how resolve this. Thanks.

---

### Post by 98174 on 2011-07-22
Linuxant drivers do not work with the 2.6.38 kernel.

---

### Post by hwertz on 2012-01-07
I'm going to take a crack at this, and hopefully have a patch later today.  I've got an Inspiron 1501 here which a relative wants specifically to use for dialup (for some reason, even though both DSL and cable are avialable there....)   (I have found where the pm_qos_etc. stuff changed -- between 2.6.34 and 2.6.35.)  They renamed pm_qos_add_requirement to pm_qos_add_request and same for pm_qos_remove.  Also rearranged the parameters just a little, so the few other pm_qos_ lines will probably have to be changed too or it'll crash even though it may compile.   Should be a short patch.

     For the linuxant driver itself I followed these instructions
[http://http://ubuntuforums.org/showthread.php?t=1781268]("http://http://ubuntuforums.org/showthread.php?t=1781268"), it appears this driver builds cleanly and is fully functional (just can't find my modem yet because of the lack of ALSA support.)

---

### Post by hwertz on 2012-01-13
OK, so I have a procedure to get alsa drivers that build.  But, they really didn't help me... I ended up with
> [   22.995113] conexant_hsfmodem_OsHdaCodecOpenDMA: modem pcm not found
[   22.995121] CAZHardware::HWInitRegs InitDMA failed status 0xc0000001 !!!
[   22.995124]
[   23.066415] cnxthsf_cnxt_serial_add: ComCtrlOpen failed (2049)
[   23.066429] conexant_init: cnxthwhda_probe() failed: -19
[   23.066570] hda_codec: cannot build controls for #0 (error -19)
[   23.072495] input: HDA ATI SB Mic at Ext Right Jack as /devices/pci0000:00/00
00:00:14.2/sound/card0/input8
[   23.072622] input: HDA ATI SB HP Out at Ext Right Jack as /devices/pci0000:00
/0000:00:14.2/sound/card0/input9

     So, the modem still does not detect.  That said...
Procedure:  


1) install the alsa-driver-linuxant.  Installation will fail.  This is fine.  It actually *installs* (in terms of placing all the packaged files where they belong) but fails at the "configure" stage (which is where it actually compiles the modules.)

2) get alsa-driver-1.0.24.tar.bz2
   Also get the patches I'll attach.  unzip them. (I was going to attach the 3 patches, but since .patch files are verboten on here, I'll zip them.  They are alsa-hda.patch, alsa.patch, and alsa-2.patch.)
     I'll assume it's going into ~/ (your home directory).  But if it's in ~/Download/, well, OK.

3) sudo -i   (everything after this has to be run as root).

4) cd /usr/lib
   tar -jxvf ~/alsa-driver-1.0.24.tar.bz2
   rm -Rv alsa-driver-linuxant
   mv alsa-driver-1.0.24 alsa-driver-linuxant

5) cd alsa-driver-linuxant

6) patch -p1 < ~/alsa-hda.patch
   patch -p0 < ~/alsa.patch
   patch -p0 < ~/alsa-2.patch
       Yes, the first patch is "-p1" and the rest are "-p0". Also, there IS a single reject in alsa.patch. That is fine, it turns out one file I patched doesn't exist yet in a "clean" copy of the alsa drivers.

7) ./configure
       (The alsa-driver-linuxant compile does run ./configure, but it doesn't get that far if it's not already configured!  Weird I know.)

8 ) dpkg-reconfigure alsa-driver-linuxant
   -or- run apt-get or synpatic or something, and it'll indicate you have a package that is installed but not configured.. this'll build the modified alsa tree, and successfully build alsa modules.

     Sound worked.  Modules all load.  But now, instead of not even trying to detect the HDA modem, it detects but fails to use it!  Well, I will tell my relative to join the 20th century (let alone the 21st) and get some cable or DSL (they live in town so they can do it.)

---

