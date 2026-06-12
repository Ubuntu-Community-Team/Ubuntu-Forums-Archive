---
title: "Synergy install probs on Warty"
date: 2005-03-02
forum: General Help
---

### Post by avantassel on 2005-03-02
I have downloaded 1.2.2 rpm v of synergy and have installed it using alien on ubuntu warty.  the install seemed to be a success.  However, i try to start the synergy client and get the following err.

synergyc: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory

I opened up the package manager and sysergy is installed as well as libstdc++5

I then installed libstdc++6 from the package manager thinking that was what it was missing but nope same error when i try to start it.

I am running this as sudo.

any help would be great.

thanks

---

### Post by Leif on 2005-03-02
I had the same problem, decided to go back to the supported version in the repositories, which works pretty ok.

---

### Post by dschep on 2005-06-29
I just installed the newer version of libc6 and synergy from the Breezy repositories (on a hoary install not breezy) and havent had any problems because of it.

---

### Post by OuchIAteMyself on 2005-07-11
[QUOTE=dschep]I just installed the newer version of libc6 and synergy from the Breezy repositories (on a hoary install not breezy) and havent had any problems because of it.[/QUOTE]


Can you please try to explain how I can do this? I edited my sources and changed the instances of Hoary to Breezy and then 

sudo apt-get -update
sudo apt-get -i

what else do I need to do now?

Sorry for the n00bishness, but thanks for the help.

---

### Post by TSJason on 2005-07-16
After the sudu apt-get update completes you just need to: sudo apt-get install synergy
and the dependencies will be downloaded and updated.  :)

---

