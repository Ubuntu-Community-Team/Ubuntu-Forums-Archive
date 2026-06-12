---
title: "Ubuntu 10.04 alsa issue"
date: 2010-05-03
forum: General Help
---

### Post by JosephMarc on 2010-05-03
Hi all,
I just recently did a clean install of ubuntu 10.04 and I must say that I am very pleased with the new improvements and optimizations. One thing that nearly didn't change though is the sound issues, though hopefully it is getting better. Now my problem is  that Ubuntu doesn't automatically detect my 5.1 setup, thus leaving me with a 2 channel system. I was able to fix this problem by manually changing the settings inside alsamixermixer : Line jack and mic jack need to be set to "Line out". The problem is that these settings revert on startup. I tried using the "alsactl store 0" command and "alsactl restore" on startup but for some obscure reason (even though both line jack and mic jack are set to "Line out") I still need to reset settings to "Line In", then reset them to "line out".

If you have any explanation for this strange behaviour or any idea on how to use 2 "alsactl store" and "alsactl restore" in conjonction (one will set to line in and the other to line out) I would be really grateful for your help.

---

### Post by agnes on 2010-05-03
I don't know why the store command doesn't work so maybe I should not reply, but perhaps you find this helpful as circumventing the manual alsamixer editing. Using [amixer]("http://linuxreviews.org/man/amixer/#lbAG") you can control alsamixer via CLI, and thus, add a startup-command that automatically sets the alsamixer settings to how you want them upon login. For your situation this would be something like
*amixer -c 0 set 'Line Jack' 'Line Out'*
(Note amixer is case sensitive and alsamixer abbreviates some control names, for the exact names of mixer controls run amixer.)

---

### Post by ubuntu27 on 2010-05-03
I wonder if [this can be]("http://www.cse.ohio-state.edu/~bondhugu/surround-pulse.shtml") of help.

---

