---
title: "a few things....gaim"
date: 2005-03-14
forum: General Help
---

### Post by Trab on 2005-03-14
well im an avid gaim user, i love it to death, but im rather hosed off about it being so outdated with its version....so from some other things ive seen ive decided to update it myself... i downloaded the gaim src rpm from their site and aliened it to make a deb.....this program didnt work (i forget the error) so i went back and got the mandrake one (something from the error tipped me off) and all seemed well, but when i tried to start gaim it gave me the error
```

tedd@raptor:~/My Downloads $ sudo dpkg -i gaim_1.1.4-1_i386.deb
(Reading database ... 90015 files and directories currently installed.)
Preparing to replace gaim 1.1.4-1 (using gaim_1.1.4-1_i386.deb) ...
Unpacking replacement gaim ...
Setting up gaim (1.1.4-1) ...

tedd@raptor:~/My Downloads $ gaim
gaim: error while loading shared libraries: libXss.so.1: cannot open shared object file: No such file or directory

```
so i then went to synaptic and had it install the warty version, it works fine now....
any help would be aprecated (about what i did wrong, and what i can do in the future...)
thank
-Trab

---

### Post by kiddo on 2005-03-14
Don't really know (I upgraded to hoary especially to have the bleeding edge gaim ;)) but I believe you need this:
sudo apt-get install libxss

Or go search for libxss in synaptic, see what the options are

That should solve the problem (remember, your output said something about a libxss-dev.thingy file missing - anyways, that's the only possible problem I can think of).

---

