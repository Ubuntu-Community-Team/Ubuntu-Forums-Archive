---
title: "vice c64 emulator - sound issue"
date: 2005-03-11
forum: General Help
---

### Post by cronos on 2005-03-11
I am new to the world of Linux, but I am really enjoying learning/using Ubuntu.  Anyway, I have downloaded Vice 64 source code, and I have compiled it using the following commands:

./configure
make
sudo make install

Now, if I type x64 in the terminal, the emulator runs, but I get a requestor saying "sound initialization failed for device 'uss'"

Have I done something wrong during the installation?  Or am I missing something?  I tried to search the forums, but without luck.  Surely, I am not the only person interested in running a c64 emulator? :)

---

### Post by fastluck on 2005-06-09
Apparently you're not that new.  I can't build it.  Here's my Make output (.configure worked just fine). Any idears?

```

root@roadrage:/usr/src/vice-1.16 # make
Making all in po
make[1]: Entering directory `/usr/src/vice-1.16/po'
make[1]: Leaving directory `/usr/src/vice-1.16/po'
Making all in src
make[1]: Entering directory `/usr/src/vice-1.16/src'
make  all-recursive
make[2]: Entering directory `/usr/src/vice-1.16/src'
Making all in resid
make[3]: Entering directory `/usr/src/vice-1.16/src/resid'
make  all-am
make[4]: Entering directory `/usr/src/vice-1.16/src/resid'
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT sid.o -MD -MP -MF ".deps/sid.Tpo" \
  -c -o sid.o `test -f 'sid.cc' || echo './'`sid.cc; \
then mv ".deps/sid.Tpo" ".deps/sid.Po"; \
else rm -f ".deps/sid.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT voice.o -MD -MP -MF ".deps/voice.Tpo" \
  -c -o voice.o `test -f 'voice.cc' || echo './'`voice.cc; \
then mv ".deps/voice.Tpo" ".deps/voice.Po"; \
else rm -f ".deps/voice.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT wave.o -MD -MP -MF ".deps/wave.Tpo" \
  -c -o wave.o `test -f 'wave.cc' || echo './'`wave.cc; \
then mv ".deps/wave.Tpo" ".deps/wave.Po"; \
else rm -f ".deps/wave.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT envelope.o -MD -MP -MF ".deps/envelope.Tpo" \
  -c -o envelope.o `test -f 'envelope.cc' || echo './'`envelope.cc; \
then mv ".deps/envelope.Tpo" ".deps/envelope.Po"; \
else rm -f ".deps/envelope.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT filter.o -MD -MP -MF ".deps/filter.Tpo" \
  -c -o filter.o `test -f 'filter.cc' || echo './'`filter.cc; \
then mv ".deps/filter.Tpo" ".deps/filter.Po"; \
else rm -f ".deps/filter.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT extfilt.o -MD -MP -MF ".deps/extfilt.Tpo" \
  -c -o extfilt.o `test -f 'extfilt.cc' || echo './'`extfilt.cc; \
then mv ".deps/extfilt.Tpo" ".deps/extfilt.Po"; \
else rm -f ".deps/extfilt.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT pot.o -MD -MP -MF ".deps/pot.Tpo" \
  -c -o pot.o `test -f 'pot.cc' || echo './'`pot.cc; \
then mv ".deps/pot.Tpo" ".deps/pot.Po"; \
else rm -f ".deps/pot.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT version.o -MD -MP -MF ".deps/version.Tpo" \
  -c -o version.o `test -f 'version.cc' || echo './'`version.cc; \
then mv ".deps/version.Tpo" ".deps/version.Po"; \
else rm -f ".deps/version.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT wave6581_PST.o -MD -MP -MF ".deps/wave6581_PST.Tpo" \
  -c -o wave6581_PST.o `test -f 'wave6581_PST.cc' || echo './'`wave6581_PST.cc; \
then mv ".deps/wave6581_PST.Tpo" ".deps/wave6581_PST.Po"; \
else rm -f ".deps/wave6581_PST.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT wave6581_PS_.o -MD -MP -MF ".deps/wave6581_PS_.Tpo" \
  -c -o wave6581_PS_.o `test -f 'wave6581_PS_.cc' || echo './'`wave6581_PS_.cc; \
then mv ".deps/wave6581_PS_.Tpo" ".deps/wave6581_PS_.Po"; \
else rm -f ".deps/wave6581_PS_.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT wave6581_P_T.o -MD -MP -MF ".deps/wave6581_P_T.Tpo" \
  -c -o wave6581_P_T.o `test -f 'wave6581_P_T.cc' || echo './'`wave6581_P_T.cc; \
then mv ".deps/wave6581_P_T.Tpo" ".deps/wave6581_P_T.Po"; \
else rm -f ".deps/wave6581_P_T.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT wave6581__ST.o -MD -MP -MF ".deps/wave6581__ST.Tpo" \
  -c -o wave6581__ST.o `test -f 'wave6581__ST.cc' || echo './'`wave6581__ST.cc; \
then mv ".deps/wave6581__ST.Tpo" ".deps/wave6581__ST.Po"; \
else rm -f ".deps/wave6581__ST.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT wave8580_PST.o -MD -MP -MF ".deps/wave8580_PST.Tpo" \
  -c -o wave8580_PST.o `test -f 'wave8580_PST.cc' || echo './'`wave8580_PST.cc; \
then mv ".deps/wave8580_PST.Tpo" ".deps/wave8580_PST.Po"; \
else rm -f ".deps/wave8580_PST.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT wave8580_PS_.o -MD -MP -MF ".deps/wave8580_PS_.Tpo" \
  -c -o wave8580_PS_.o `test -f 'wave8580_PS_.cc' || echo './'`wave8580_PS_.cc; \
then mv ".deps/wave8580_PS_.Tpo" ".deps/wave8580_PS_.Po"; \
else rm -f ".deps/wave8580_PS_.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT wave8580_P_T.o -MD -MP -MF ".deps/wave8580_P_T.Tpo" \
  -c -o wave8580_P_T.o `test -f 'wave8580_P_T.cc' || echo './'`wave8580_P_T.cc; \
then mv ".deps/wave8580_P_T.Tpo" ".deps/wave8580_P_T.Po"; \
else rm -f ".deps/wave8580_P_T.Tpo"; exit 1; \
fi
if g++ -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DPACKAGE=\"resid\" -DVERSION=\"0.16vice\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DSIZEOF_INT=4  -I. -I.     -g -Wall -O2 -funroll-loops -fomit-frame-pointer -fno-exceptions -MT wave8580__ST.o -MD -MP -MF ".deps/wave8580__ST.Tpo" \
  -c -o wave8580__ST.o `test -f 'wave8580__ST.cc' || echo './'`wave8580__ST.cc; \
then mv ".deps/wave8580__ST.Tpo" ".deps/wave8580__ST.Po"; \
else rm -f ".deps/wave8580__ST.Tpo"; exit 1; \
fi
rm -f libresid.a
ar cru libresid.a sid.o voice.o wave.o envelope.o filter.o extfilt.o pot.o version.o wave6581_PST.o wave6581_PS_.o wave6581_P_T.o wave6581__ST.o wave8580_PST.o wave8580_PS_.o wave8580_P_T.o wave8580__ST.o
ranlib libresid.a
make[4]: Leaving directory `/usr/src/vice-1.16/src/resid'
make[3]: Leaving directory `/usr/src/vice-1.16/src/resid'
Making all in sounddrv
make[3]: Entering directory `/usr/src/vice-1.16/src/sounddrv'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/sounddrv'
Making all in drive
make[3]: Entering directory `/usr/src/vice-1.16/src/drive'
Making all in iec
make[4]: Entering directory `/usr/src/vice-1.16/src/drive/iec'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/src/vice-1.16/src/drive/iec'
Making all in iec128dcr
make[4]: Entering directory `/usr/src/vice-1.16/src/drive/iec128dcr'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/src/vice-1.16/src/drive/iec128dcr'
Making all in iecieee
make[4]: Entering directory `/usr/src/vice-1.16/src/drive/iecieee'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/src/vice-1.16/src/drive/iecieee'
Making all in ieee
make[4]: Entering directory `/usr/src/vice-1.16/src/drive/ieee'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/src/vice-1.16/src/drive/ieee'
Making all in tcbm
make[4]: Entering directory `/usr/src/vice-1.16/src/drive/tcbm'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/usr/src/vice-1.16/src/drive/tcbm'
make[4]: Entering directory `/usr/src/vice-1.16/src/drive'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/src/vice-1.16/src/drive'
make[3]: Leaving directory `/usr/src/vice-1.16/src/drive'
Making all in vdrive
make[3]: Entering directory `/usr/src/vice-1.16/src/vdrive'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/vdrive'
Making all in fsdevice
make[3]: Entering directory `/usr/src/vice-1.16/src/fsdevice'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/fsdevice'
Making all in diskimage
make[3]: Entering directory `/usr/src/vice-1.16/src/diskimage'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/diskimage'
Making all in iecbus
make[3]: Entering directory `/usr/src/vice-1.16/src/iecbus'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/iecbus'
Making all in serial
make[3]: Entering directory `/usr/src/vice-1.16/src/serial'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/serial'
Making all in parallel
make[3]: Entering directory `/usr/src/vice-1.16/src/parallel'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/parallel'
Making all in tape
make[3]: Entering directory `/usr/src/vice-1.16/src/tape'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/tape'
Making all in imagecontents
make[3]: Entering directory `/usr/src/vice-1.16/src/imagecontents'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/imagecontents'
Making all in fileio
make[3]: Entering directory `/usr/src/vice-1.16/src/fileio'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/fileio'
Making all in video
make[3]: Entering directory `/usr/src/vice-1.16/src/video'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/video'
Making all in raster
make[3]: Entering directory `/usr/src/vice-1.16/src/raster'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/raster'
Making all in vicii
make[3]: Entering directory `/usr/src/vice-1.16/src/vicii'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/vicii'
Making all in vdc
make[3]: Entering directory `/usr/src/vice-1.16/src/vdc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/vdc'
Making all in crtc
make[3]: Entering directory `/usr/src/vice-1.16/src/crtc'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/crtc'
Making all in gfxoutputdrv
make[3]: Entering directory `/usr/src/vice-1.16/src/gfxoutputdrv'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/gfxoutputdrv'
Making all in printerdrv
make[3]: Entering directory `/usr/src/vice-1.16/src/printerdrv'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/printerdrv'
Making all in rs232drv
make[3]: Entering directory `/usr/src/vice-1.16/src/rs232drv'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/rs232drv'
Making all in sid
make[3]: Entering directory `/usr/src/vice-1.16/src/sid'
if g++ -DHAVE_CONFIG_H -I. -I. -I../../src -I../../src/arch/unix -I../../src/resid -I../../src -I../../src  -I/usr/X11R6/include  -g -O2 -DNO_REGPARM -Wall -Wstrict-prototypes -Winline -fno-exceptions -MT resid.o -MD -MP -MF ".deps/resid.Tpo" \
  -c -o resid.o `test -f 'resid.cc' || echo './'`resid.cc; \
then mv ".deps/resid.Tpo" ".deps/resid.Po"; \
else rm -f ".deps/resid.Tpo"; exit 1; \
fi
rm -f libsid.a
ar cru libsid.a fastsid.o sid-cmdline-options.o sid-resources.o sid-snapshot.o sid.o resid.o
ranlib libsid.a
make[3]: Leaving directory `/usr/src/vice-1.16/src/sid'
Making all in monitor
make[3]: Entering directory `/usr/src/vice-1.16/src/monitor'
make  all-am
make[4]: Entering directory `/usr/src/vice-1.16/src/monitor'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/usr/src/vice-1.16/src/monitor'
make[3]: Leaving directory `/usr/src/vice-1.16/src/monitor'
Making all in core
make[3]: Entering directory `/usr/src/vice-1.16/src/core'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/core'
Making all in c64
make[3]: Entering directory `/usr/src/vice-1.16/src/c64'
make  all-recursive
make[4]: Entering directory `/usr/src/vice-1.16/src/c64'
Making all in cart
make[5]: Entering directory `/usr/src/vice-1.16/src/c64/cart'
make[5]: Nothing to be done for `all'.
make[5]: Leaving directory `/usr/src/vice-1.16/src/c64/cart'
make[5]: Entering directory `/usr/src/vice-1.16/src/c64'
make[5]: Nothing to be done for `all-am'.
make[5]: Leaving directory `/usr/src/vice-1.16/src/c64'
make[4]: Leaving directory `/usr/src/vice-1.16/src/c64'
make[3]: Leaving directory `/usr/src/vice-1.16/src/c64'
Making all in c128
make[3]: Entering directory `/usr/src/vice-1.16/src/c128'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/c128'
Making all in vic20
make[3]: Entering directory `/usr/src/vice-1.16/src/vic20'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/vic20'
Making all in pet
make[3]: Entering directory `/usr/src/vice-1.16/src/pet'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/pet'
Making all in plus4
make[3]: Entering directory `/usr/src/vice-1.16/src/plus4'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/plus4'
Making all in cbm2
make[3]: Entering directory `/usr/src/vice-1.16/src/cbm2'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/usr/src/vice-1.16/src/cbm2'
Making all in arch
make[3]: Entering directory `/usr/src/vice-1.16/src/arch'
Making all in unix
make[4]: Entering directory `/usr/src/vice-1.16/src/arch/unix'
Making all in x11
make[5]: Entering directory `/usr/src/vice-1.16/src/arch/unix/x11'
Making all in xaw
make[6]: Entering directory `/usr/src/vice-1.16/src/arch/unix/x11/xaw'
Making all in widgets
make[7]: Entering directory `/usr/src/vice-1.16/src/arch/unix/x11/xaw/widgets'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../../../../../src -I../../../../../../src/arch/unix -I../../../../../../src -I../../../../../../src -I../../../../../../src/arch/unix/x11 -I../../../../../../src/arch/unix/x11/xaw  -I/usr/X11R6/include  -g -O2 -DNO_REGPARM -Wall -Wstrict-prototypes -Winline -MT FileSel.o -MD -MP -MF ".deps/FileSel.Tpo" \
  -c -o FileSel.o `test -f 'FileSel.c' || echo './'`FileSel.c; \
then mv ".deps/FileSel.Tpo" ".deps/FileSel.Po"; \
else rm -f ".deps/FileSel.Tpo"; exit 1; \
fi
FileSel.c:47:29: X11/Xaw/SimpleP.h: No such file or directory
FileSel.c:48:28: X11/Xaw/Simple.h: No such file or directory
FileSel.c:49:28: X11/Xaw/LabelP.h: No such file or directory
FileSel.c:50:27: X11/Xaw/Label.h: No such file or directory
FileSel.c:51:30: X11/Xaw/CommandP.h: No such file or directory
FileSel.c:52:29: X11/Xaw/Command.h: No such file or directory
FileSel.c:53:27: X11/Xaw/FormP.h: No such file or directory
FileSel.c:54:26: X11/Xaw/Form.h: No such file or directory
In file included from FileSelP.h:25,
                 from FileSel.c:71:
DirMgr.h:86: warning: function declaration isn't a prototype
In file included from FileSel.c:71:
FileSelP.h:27:31: X11/Xaw/Cardinals.h: No such file or directory
FileSel.c: In function `ChildrenCreate':
FileSel.c:711: error: `labelWidgetClass' undeclared (first use in this function)
FileSel.c:711: error: (Each undeclared identifier is reported only once
FileSel.c:711: error: for each function it appears in.)
FileSel.c:749: error: `commandWidgetClass' undeclared (first use in this function)
make[7]: *** [FileSel.o] Error 1
make[7]: Leaving directory `/usr/src/vice-1.16/src/arch/unix/x11/xaw/widgets'
make[6]: *** [all-recursive] Error 1
make[6]: Leaving directory `/usr/src/vice-1.16/src/arch/unix/x11/xaw'
make[5]: *** [all-recursive] Error 1
make[5]: Leaving directory `/usr/src/vice-1.16/src/arch/unix/x11'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/usr/src/vice-1.16/src/arch/unix'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/usr/src/vice-1.16/src/arch'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/usr/src/vice-1.16/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/usr/src/vice-1.16/src'
make: *** [all-recursive] Error 1
root@roadrage:/usr/src/vice-1.16 #                        
```

---

### Post by fastluck on 2005-06-10
Here's what I did, and it fixed the problem for me.

In Control Center -> Sound System: I switched to Open Sound System.

It worked after that, except I still get the error if I try to run two emulators simultaneously.

I tried Autodetect, but it didn't work.  So I guess now EVERYTHING runs through OSS emulation, or does is Alsa by itself activated when something needs Alsa and not OSS?

---

### Post by fif on 2005-11-05
For FastLuck, try ./configure --enable-gnomeui
I had the same problem and it worked for me.

HTH

---

