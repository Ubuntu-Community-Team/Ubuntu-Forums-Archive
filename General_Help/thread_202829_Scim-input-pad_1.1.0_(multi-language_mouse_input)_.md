---
title: "Scim-input-pad 1.1.0 (multi-language mouse input) cannot get to work"
date: 2006-06-24
forum: General Help
---

### Post by hob4bit on 2006-06-24
Hi, I am running Ubuntu-6.06. I am also using SCIM the multi-language input method.
I am interested in entering Chinese and think the "scim-input-pad" input engine
which is a multi-language input system that uses the mouse (a bit like the XP mouse
input pad for Chinese).

libscim8c2a               1.4.4-1ubuntu12   992KB library for SCIM platform
scim                      1.4.4-1ubuntu12  1872KB smart common input method platform
scim-gtk2-immodule        1.4.4-1ubuntu12   312KB GTK+2 input method module with SCIM as backend
scim-modules-socket       1.4.4-1ubuntu12   284KB socket modules for SCIM platform
scim-modules-table        0.5.6-1build1     996KB generic tables IM engine module for SCIM platform
scim-pinyin               0.5.91-0ubuntu3  5344KB smart pinyin IM engine for SCIM platform
scim-tables-zh            0.5.6-1build1   12000KB Chinese input method data tables for SCIM platform[/SIZE][/SIZE][/SIZE]

I cannot find "scim-input-pad" in the Ubuntu-6.06 reposy. So I downloaded it and tried
to compile it. It fails:


checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for an ANSI C-conforming const... (cached) yes
checking for inline... (cached) inline
checking for size_t... (cached) yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for SCIM... configure: error: Package requirements (scim >= 1.2.0) were not met.
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively you may set the SCIM_CFLAGS and SCIM_LIBS environment variables
to avoid the need to call pkg-config.  See the pkg-config man page for
more details.
make: *** No targets specified and no makefile found.  Stop.
hobs@doraemon_$ 

Has anybody got "scim-input-pad" to work in Ubuntu-6.06? I don;t understand what
to do with SCIM_CFLAGS and SCIM_LIBS mean and how to set them. is there
a way to ask for an extra SCIM input method to be ported and added to the Ubuntu
reposy?

Thanks

---

### Post by hob4bit on 2006-07-08
Hello, I am wondering whether anybody has tried the alternative 
"chinput 3.0" in Ubuntu 6.06. I can install it but cannot work out 
how to use it.

Thanks

---

