---
title: "Unable to install realplayer10"
date: 2006-05-12
forum: General Help
---

### Post by banksw on 2006-05-12
Newbie to Ubuntu -linux.  Two bin files from realaudio one with a -1 version.

and following resulted from ter mode.

banksw@Dell400gs:~/Desktop$ chmod +x RealPlayer10GOLD.bin
banksw@Dell400gs:~/Desktop$ sudo ./RealPlayer10GOLD.bin
Password:
Sorry, try again.
Password:
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: ca nnot open shared object file: No such file or directory
banksw@Dell400gs:~/Desktop$ chmod a+x RealPlayer10GOLD-1.bin
banksw@Dell400gs:~/Desktop$ sudo ./RealPlayer10GOLD-1.bin
./RealPlayer10GOLD-1.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared o bject file: No such file or directory
banksw@Dell400gs:~/Desktop$

not sure why it does not load?

---

### Post by meng on 2006-05-12
You probably need to:
**sudo apt-get install libstdc++5**
first.

Check out:
[https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28realplayer%29]("https://wiki.ubuntu.com/RealplayerInstallationMethods?highlight=%28realplayer%29")

---

