---
title: "Real newbie question on compiling"
date: 2009-09-01
forum: General Help
---

### Post by 1ronlung on 2009-09-01
Hi.
I'm trying to compile some homebrew for my wii.
Directory looks as follows :

```

config.h     LICENCE.TXT                     Makefile.sft_gfx_wii
debugger     logo.xpm                        mupen64.ini
doc          main                            mupen64_soft_gfx
fileBrowser  Makefile.GLN64_dev              ogc_patches
gc_audio     Makefile.GLN64_dev_new-ppc      PC
gc_input     Makefile.GLN64_dev_wii          r4300
gc_memory    Makefile.GLN64_dev_wii_new-ppc  README
glN64_GX     Makefile.GX_gfx                 rsp_hle
gui          Makefile.GX_gfx_wii             rsp_hle-ppc
GX_gfx       Makefile.sft_gfx

```

The makefiles I need are already there and appear to be made:

```

root@HAL9000:/home/mark/Documents/Wii64# make *.*
make: Nothing to be done for `config.h'.
make: Nothing to be done for `LICENCE.TXT'.
make: Nothing to be done for `logo.xpm'.
make: Nothing to be done for `Makefile.GLN64_dev'.
make: Nothing to be done for `Makefile.GLN64_dev_new-ppc'.
make: Nothing to be done for `Makefile.GLN64_dev_wii'.
make: Nothing to be done for `Makefile.GLN64_dev_wii_new-ppc'.
make: Nothing to be done for `Makefile.GX_gfx'.
make: Nothing to be done for `Makefile.GX_gfx_wii'.
make: Nothing to be done for `Makefile.sft_gfx'.
make: Nothing to be done for `Makefile.sft_gfx_wii'.
make: Nothing to be done for `mupen64.ini'.

```

I'm trying to produce a .ELF or .DOL file.

What's my next step ?

make install returns:
root@HAL9000:/home/mark/Documents/Wii64# make install
make: *** No rule to make target `install'.  Stop.

Sorry for my lack of knowledge, but I'm new to this and my experience is limited to config, make, make install ;)

---

### Post by 1ronlung on 2009-09-01
*bump*

Have been at this general issue now for hours..  Please advise if poss ,,

---

### Post by denver on 2009-09-02
You might have better luck if you give the README file a try. Also, you might have a lot more luck getting an answer on nintendo wii support forums. People there are likely to have had more experience in this regard.

The "make" command usually need a "Makefile" file in the current working directory. You might also need to cross compile if the Wii is not x86. Like i said, might have better luck on Wii support forums.

---

