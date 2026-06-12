---
title: "Thc hydra"
date: 2010-03-28
forum: General Help
---

### Post by mafiamade on 2010-03-28
Okay i'm having trouble with the installation process of THC HYDRA, it's my first time using it, someone was telling me about THC HYDRA GTK??!? 
 
I managed to get THC HYDRA running in CMD, but i want to use THC HYDRA GTK and i dont get how to get it working...
 
I checked the main site of THC HYDRA, and it has screenshots of GTK but i dont know how to get it like that..for me im only working in CMD...

---

### Post by snoopy-2009 on 2011-04-01
im having the same issue... i somehow managed to lock myself out of an entire drive with ubuntu's drive encryption. im damn sure i didn't change the pw from the one i have written down, yet after a fresh install of ubuntu (for a separate purpose) i cannot get past my first encryption. sooo im trying to see if hydra will work on it, with a self-made list of close pws, caps differential, etc.. 

BUT not the point.. 

ive read that were supposed to run xhydra for the GUI, but this just feeds out "command not found" 

very confused.. not understanding why it wasn't compiled with the latest source from their site....:confused::confused::confused:

---

### Post by snoopy-2009 on 2011-04-01
well, i feel like a fool.. just after posting my last.. i glanced over at the hydra src dir i still had open, and noticed the /hydra-gtk dir. 

i then switched to my terminal, and moved into that dir, and ran ./configure, which stopped with notices informing me i need "gtk+-2.0" to be installed.. so i ran

```
 sudo apt-get install gtk+-2.0
```

which resulted in the same msg....

```
checking for gtk+-2.0 >= 2.0.0... Package gtk+-2.0 was not found in the pkg-config search path. Perhaps you should add the directory containing `gtk+-2.0.pc' to the PKG_CONFIG_PATH environment variable No package 'gtk+-2.0' found
configure: error: Library requirements (gtk+-2.0 >= 2.0.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.
tech_support@1337b0x:~/Downloads/hydra-6.1-src/hydra-gtk$ 

```


i dont know if im in the right direction or not.. thought i was on a roll for a moment.. lol.. i figured gtk would install and id be all set to continue..

---

### Post by atomicben on 2011-08-03
If you got (the command line) hydra compiled and installed there is nothing extra you need to do to use the GUI (provided there were no compile errors).

Press ALT+F2
type in xhydra
press enter

of course you can make yourself a shortcut under your menu if you want.

---

