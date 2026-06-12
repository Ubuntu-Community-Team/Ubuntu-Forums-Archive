---
title: "problems with Sudo?"
date: 2006-02-08
forum: General Help
---

### Post by KevNice on 2006-02-08
OK, I am following the users guide instructions on how to install realplayer. I finally figured out how to locate and navigate around, but when I go to execute the realplayer file to install it (using the syntax given to me in the starters guide), this happened:

kevin@softbank:~$ chmod +x RealPlayer10GOLD.bin
kevin@softbank:~$ sudo ./RealPlayer10GOLD.bin
Password:
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

After I typed in my password, I got the above error message. Is sudo not working right or did I do it wrong?

---

### Post by frodon on 2006-02-08
No problem with sudo here, you might not have the libstdc installed and this why you get this error message because the system can't find the file related to this library.
Install libstdc and your problem should be solved .... i hope

---

### Post by equal on 2006-02-08
yeah try this:
```
sudo apt-get install libstdc++.so.5
```

if that doesn't work, try going into System > Administration > Synaptic Package Manager, and do a search for libstdc++ and see what comes up.

---

### Post by KevNice on 2006-02-08
thanks for the help, guys. that version of libstdc wasnt in my repository for some reason, so I just downloaded any files in that directory with the name libstdcc in it and installed them, and ran it again and it worked fine. thanks!

---

