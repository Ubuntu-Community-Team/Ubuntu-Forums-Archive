---
title: "Synaptic Package Manager Problem"
date: 2009-08-03
forum: General Help
---

### Post by VistaFTL on 2009-08-03
```
E: Type '--2009-08-03' is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
```Whenever i try to open Synaptic Package Manager its tells me that, im a noob on ubuntu and im wishing id stayed with vista because i never had ANY of these sort of problems with it. Even so, please help me :( 

PS. I am also getting this error when i try to open "Add/Remove Applications"

```
This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
```ill love you foreva if you help me :)

---

### Post by physic.dude on 2009-08-03
Well if it isn't to much of a hassle, and if you don't have very many important things on ubuntu, then all I can say is to reinstall ubuntu all together. Since it looks like you have some bad packages, perhaps due to a bad mishap in the ubuntu install process.

---

### Post by snowpine on 2009-08-03
It looks like you created a file called /etc/apt/sources.list.d/winehq.list (this file is not part of the default Ubuntu install) and something is wrong with it. Try to retrace your steps and figure out where things went wrong... maybe you followed a tutorial to install Wine and you missed a step?

---

### Post by oldos2er on 2009-08-03
Please post the output of this command: **cat /etc/apt/sources.list.d/winehq.list**

---

### Post by kayvortex on 2009-08-03
The information that synaptic (and all apt-based tools) needs to work is stored in the folder /etc/apt. Now, the error you posted indicates that there is an error in the file /etc/apt/sources.list.d/winehq.list (on line 1). Files in the directory /etc/apt/sources.list.d are read by programs like synaptic and tell it where it can find programs to download and install. Like *snowpine* said, that file is not usually present on a new system; so either you have, or a program you installed and ran has, added it. It's not really a problem to fix, we just need to see what's in it: run the command that *oldos2er* mentioned, and we can go from there.

---

