---
title: "Which kernel modules are running??"
date: 2006-02-22
forum: General Help
---

### Post by bigblop on 2006-02-22
Is there some command that I can run to see which kernel modules are running when I use Ubuntu? I know they are in the /etc/modules file, but I would like to confirm that they are running...

---

### Post by oakz on 2006-02-22
lsmod

---

### Post by heimo on 2006-02-22
lsmod lists modules that are loaded and shows if they're in use (those with number 0 can be removed using rmmod).

---

### Post by kaamos on 2006-02-22
"lsmod" is the one you are looking for. If you know the module name you can save the trouble of scrollin through output with "lsmod | grep the_name"

---

### Post by breezyfox on 2006-02-22
[QUOTE=bigblop]Is there some command that I can run to see which kernel modules are running when I use Ubuntu? ...[/QUOTE]

use the following command:

uname -r

"latest stable breezy kernel is 2.6.12-10".

bz

---

### Post by dcstar on 2006-02-23
[QUOTE=heimo]lsmod lists modules that are loaded and shows if they're in use (those with number 0 can be removed using rmmod).[/QUOTE]
Eh?, AFAIK the number 0 means that the particular module doesn't have any other module dependencies for it to be loaded, but other modules may depend on it.

Remove them at your peril.

---

### Post by heimo on 2006-02-23
[quote=dcstar]Eh?, AFAIK the number 0 means that the particular module doesn't have any other module dependencies for it to be loaded, but other modules may depend on it.

Remove them at your peril.[/quote] 
I should probably rephrase what I meant by "can be removed". If the number is other than 0, it's in use by other module and can't be removed. It doesn't mean that the module is useless and it should be removed.

---

### Post by heimo on 2006-02-23
My explanation above isn't quite exact... But I'll give an example. No USB storage devices mounted, run lsmod, mount an USB memory stick, run lsmod. Difference in my system (lines without changes omitted):

before: 
```
usb_storage            79488  0
sd_mod                 20448  4

``` 
after:
```
usb_storage            79488  1
sd_mod                 20448  6
[COLOR=Lime]nls_iso8859_1           4224  1
nls_cp437               5888  1
vfat                   14496  1
fat                    55548  1 vfat[/COLOR]

``` 
[COLOR=Lime]new modules[/COLOR]

Unmount the stick and the new modules will still be there, but with 0 indicating they're no longer used, but still loaded. Those modules can be removed now, and they'll get loaded when needed. List of modules after the number indicate which modules require the module (above vfat relies on fat).

---

