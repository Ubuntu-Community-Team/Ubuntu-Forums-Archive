---
title: "Update manager triggers issue"
date: 2010-07-13
forum: General Help
---

### Post by iamfuzzeh on 2010-07-13
Right, i've searched all over here and on google and tried several solutions but to no avail, so i decided to ask you guys for help. Moving on to the issue, everything was cool until a few days ago when update manager stoped working. I open it, it searches for upates, and shows me the list without breaking a sweat, but after i press update it downloads everything and gives me an error. Without further delay, this is it:

A extrair templates a partir dos pacotes: 100%
A pré-configurar os pacotes...
dpkg: erro de sintaxe no ficheiro de 'triggers' adiados '/var/lib/dpkg/triggers/Unincorp' no carácter 'U' midline
E: Sub-process /usr/bin/dpkg returned an error code (2)
Um pacote falhou ao instalar. A tentar recuperar...
dpkg: erro de sintaxe no ficheiro de 'triggers' adiados '/var/lib/dpkg/triggers/Unincorp' no carácter 'U' midline.

I know it's in Portuguese, but it basically says "sintax error in 'triggers' file postponed '/var/lib/dpkg/triggers/Unincorp' in the midline 'U' character."
Any chance you guys can help me out ?

---

### Post by tgrego on 2010-07-13
did you check if there is any broken package you need to solve first?
check in the Custom Filters tab of synaptic manager...

It may also been just a problem with the server you are using in synaptic, did you try the main server to check if the same error happens?

---

### Post by iamfuzzeh on 2010-07-13
Yeah, i tried to use the fix broken packages option in synaptic, it didn't do anything, and there's nothing in the Broken filter.
Also yes, i switched from the Portugal server to the main one, still the same.

---

### Post by hawthornso23 on 2010-07-13
I don't know the cause of the problem, but it is telling you where to look. Try

gedit  /var/lib/dpkg/triggers/Unincorp

and see what is in there. Maybe there is an obvious syntax error you can fix which will help it complete the update. This file is empty on my system.

---

### Post by iamfuzzeh on 2010-07-13
It's empty on your system ? Look at mine:

Package: libc-bin
Status: install ok triggers-pending
Priority: required
Section: libs
Installed-Size: 1552
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: eglibc
Version: 2.11.1-0ubuntu7.1
Replaces: libc0.1, libc0.3, libc6, libc6.1
Breaks: libc0.1 (<< 2.10), libc0.3 (<< 2.10), libc6 (<< 2.10), libc6.1 (<< 2.10)
Conffiles:
 /etc/bindresvport.blacklist 154db0e55fa99051ff1bd99e5b2c0584
 /etc/ld.so.conf.d/libc.conf d4d833fd095fb7b90e1bb4a547f16de6
 /etc/gai.conf 4b3389be7132a6a8805f3df8d0ff00f6
Description: Embedded GNU C Library: Binaries
 This package contains utility programs related to the GNU C Library.
 .
  * catchsegv: catch segmentation faults in programs
  * getconf: query system configuration variables
  * getent: get entries from administrative databases
  * iconv, iconvconfig: convert between character encodings
  * ldd, ldconfig: print/configure shared library dependencies
  * locale, localedef: show/generate locale definitions
  * rpcinfo: report RPC information
  * tzselect, zdump, zic: select/dump/compile time zones
Triggers-Pending: ldconfig
Homepage: [http://www.eglibc.org](http://www.eglibc.org)
Original-Maintainer: GNU Libc Maintainers <debian-glibc@lists.debian.org>

EDIT: I copied and pasted everything inside it in a text file just in case this does more harm than good, but after that i completely cleared it, saved it, and now i'm currently attempting the updates, i'll get back to you guys in a sec.

EDIT2: It appears to have worked, i'll reboot to finish everything off and return with a definite answer, however i do think it worked.

Third and final edit
Everything has been updated and all is working correctly, thank you for the help guys, i really apreciate it.

---

### Post by hawthornso23 on 2010-07-13
Good work iamfuzzeh. Well done.

---

