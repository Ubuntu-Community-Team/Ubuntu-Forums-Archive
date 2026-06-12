---
title: "Trouble with opening Gnucash"
date: 2010-02-27
forum: General Help
---

### Post by techiewannabe on 2010-02-27
I am having difficulty opening up Gnucash which I (thought) had been properly installed. When I try to open it, I see the an icon that appears like it is opening the program, but then nothing opens up. I have tried to uninstall it; I've removed it and reinstalled it. I've looked at Synaptic to see whether there are any related residual files and found none.

I am running Jaunty on a Compaq Presario R3000 laptop.

Your help, please.

Thanks.

---

### Post by oldfred on 2010-02-27
I run from an icon but run it from the terminal and see what it says.
Mine return this but I guess these are ok.
fred@fred-laptop:~$ gnucash
gnc.bin-Message: main: binreloc relocation support was disabled at configure time.

Found Finance::Quote version 1.16
gwenhywfar-INFO: plugin.c:  584: Plugin type "ct" unregistered
gwenhywfar-INFO: plugin.c:  584: Plugin type "configmgr" unregistered
gwenhywfar-INFO: plugin.c:  584: Plugin type "dbio" unregistered
fred@fred-laptop:~$

---

### Post by techiewannabe on 2010-02-27
Oldfred:
Thanks for your suggestion. When I tried to load from the terminal, I got the following message:  

tom@Compaq:~$ gnucash
gnucash-bin: error while loading shared libraries: libgsf-gnome-1.so.114: cannot open shared object file: No such file or directory

Any ideas on dealing with this?

Thanks.

Techiewannabe.

---

### Post by techiewannabe on 2010-02-27
I was able to solve this problem by finding the missing file (libgsf-gnome-1) in Synaptic. I installed that file and Gnucash is now accessible.

Techiewannabe

---

