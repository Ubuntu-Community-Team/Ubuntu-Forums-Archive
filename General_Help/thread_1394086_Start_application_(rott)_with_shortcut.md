---
title: "Start application (rott) with shortcut"
date: 2010-01-30
forum: General Help
---

### Post by andlinux on 2010-01-30
I have the open source version of Rise of the Triad for linux.
If I open rott in a terminal then I go tp the directory where the file is standing and do ./rott.

Now I want to make a shortcut on my desktop and if I putt ```
~/Games/rott-1.1.1/rott$ ./rott
```
in the shortcut then it won't start.

What can I do to start it with a shortcut.

---

### Post by oldos2er on 2010-01-30
I think the launcher needs an absolute path, e.g. /home/user/rott-1.1.1/rott/rott

---

### Post by andlinux on 2010-01-30
> **oldos2er said:**
> I think the launcher needs an absolute path, e.g. /home/user/rott-1.1.1/rott/rott

Even that didn't work. I just tested it.

---

### Post by oldos2er on 2010-01-30
Did you replace *user* with your username?

---

### Post by andlinux on 2010-01-31
> **oldos2er said:**
> Did you replace *user* with your username?

Yes, like this:

```
/home/andy/Games/rott-1.1.1/rott/rott
```

---

### Post by oldos2er on 2010-01-31
Can you post the output of **ls ~/Games/rott-1.1.1** ?

---

### Post by andlinux on 2010-01-31
> **oldos2er said:**
> Can you post the output of **ls ~/Games/rott-1.1.1** ?
ls ~/Games/rott-1.1.1
```
COPYING  doc  mac  misc  README  rott  vs.net
```

```
ls /home/andy/Games/rott-1.1.1/rott/
audiolib     fli_glob.h   rt_build.o  rt_floor.o  rt_sc_a.h   rt_util.h
byteordr.c   fli_main.c   _rt_buil.h  rt_game.c   rt_scale.c  rt_util.o
byteordr.h   fli_main.h   rt_cfg.c    _rt_game.h  rt_scale.h  rt_vh_a.h
byteordr.o   fli_type.h   rt_cfg.h    rt_game.h   rt_scale.o  rt_vid.c
cin_actr.c   fli_util.c   rt_cfg.o    rt_game.o   _rt_scal.h  _rt_vid.h
cin_actr.h   fli_util.h   rt_com.c    rt_in.c     rt_sound.c  rt_vid.h
cin_actr.o   f_scale.h    _rt_com.h   _rt_in.h    rt_sound.h  rt_vid.o
cin_def.h    fx_man.c     rt_com.h    rt_in.h     rt_sound.o  rt_view.c
cin_efct.c   fx_man.h     rt_com.o    rt_in.o     _rt_soun.h  rt_view.h
cin_efct.h   gmove.h      rt_crc.c    rt_main.c   _rt_spba.h  rt_view.o
cin_efct.o   isr.c        rt_crc.h    _rt_main.h  rt_spbal.c  sbconfig.c
cin_evnt.c   _isr.h       rt_crc.o    rt_main.h   rt_spbal.h  sbconfig.h
cin_evnt.h   isr.h        rt_debug.c  rt_main.o   rt_spbal.o  scriplib.c
cin_evnt.o   isr.o        rt_debug.h  rt_map.c    rt_sqrt.c   scriplib.h
cin_glob.c   keyb.h       rt_debug.o  _rt_map.h   rt_sqrt.h   scriplib.o
cin_glob.h   lookups.c    rt_def.h    rt_map.h    rt_sqrt.o   sndcards.h
cin_glob.o   lumpy.h      rt_dmand.c  rt_map.o    rt_stat.c   snd_reg.h
cin_main.c   Makefile     rt_dmand.h  rt_menu.c   rt_state.c  snd_shar.h
cin_main.h   memcheck.h   rt_dmand.o  _rt_menu.h  rt_state.o  splib.h
cin_main.o   modexlib.c   _rt_dman.h  rt_menu.h   _rt_stat.h  sprites.h
cin_util.c   modexlib.h   rt_door.c   rt_menu.o   rt_stat.h   states.h
cin_util.h   modexlib.o   _rt_door.h  rt_msg.c    rt_stat.o   task_man.h
cin_util.o   music.h      rt_door.h   _rt_msg.h   rt_str.c    version.h
DARKWAR.RTC  myprint.h    rt_door.o   rt_msg.h    _rt_str.h   watcom.c
DARKWAR.RTL  profile.h    rt_dr_a.h   rt_msg.o    rt_str.h    watcom.h
DARKWAR.WAD  REMOTE1.RTS  rt_draw.c   rt_net.c    rt_str.o    watcom.o
develop.h    rott         _rt_draw.h  _rt_net.h   _rt_swft.h  winrott.c
develop.h~   rottnet.h    rt_draw.h   rt_net.h    rt_swift.c  WinRott.h
dosutil.c    _rt_acto.h   rt_draw.o   rt_net.o    rt_swift.h  winrott.o
dosutil.o    rt_actor.c   rt_err.c    _rt_play.h  rt_swift.o  w_wad.c
dukemusc.c   rt_actor.h   rt_err.o    rt_playr.c  rt_table.h  _w_wad.h
dukemusc.o   rt_actor.o   rt_error.c  rt_playr.h  rt_ted.c    w_wad.h
engine.c     rt_battl.c   rt_error.h  rt_playr.o  _rt_ted.h   w_wad.o
_engine.h    rt_battl.h   rt_fc_a.h   rt_rand.c   rt_ted.h    z_zone.c
engine.h     rt_battl.o   _rt_floo.h  _rt_rand.h  rt_ted.o    _z_zone.h
engine.o     rt_build.c   rt_floor.c  rt_rand.h   rt_util.c   z_zone.h
fli_def.h    rt_build.h   rt_floor.h  rt_rand.o   _rt_util.h  z_zone.o
```

---

### Post by oldos2er on 2010-01-31
Oh, you've compiled the source code? Have you run sudo make install?

---

### Post by andlinux on 2010-01-31
> **oldos2er said:**
> Oh, you've compiled the source code? Have you run sudo make install?
yes I compiled it but I can't remember that I did "sudo make install", I just tried to do "sudo make install" but I get an error message.

It's telling me there is no line to make install.

Edit: this is standing in the readme file:
```

To compile the source code under Linux, change to the rott/ directory and type:

make clean
make

```

---

### Post by oldos2er on 2010-01-31
If **make** completed without errors, **sudo make install** should install rott to /usr/local/bin

---

### Post by andlinux on 2010-02-02
> **oldos2er said:**
> If **make** completed without errors, **sudo make install** should install rott to /usr/local/bin

Sorry for the late reply but that's what I get and make completed without errors.

---

