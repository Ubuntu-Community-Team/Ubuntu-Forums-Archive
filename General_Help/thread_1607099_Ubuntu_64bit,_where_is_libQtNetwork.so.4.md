---
title: "Ubuntu 64bit, where is libQtNetwork.so.4?"
date: 2010-10-27
forum: General Help
---

### Post by bFr-33 on 2010-10-27
Hello!

Ok, I have one problem with the program called skype-called-recorder....It just doesn't open...
And the terminal says: skype-call-recorder: error while loading shared libraries: libQtNetwork.so.4: cannot open shared object file: No such file or directory

So, I guess the problem is this libqtnetwork.so.4...but I don't know what to do to fix it.

Can you help me please?! :(

My ubuntu version is the 10.10 64bit.

Thank you.

---

### Post by bFr-33 on 2010-10-27
Help me please!

---

### Post by bFr-33 on 2010-10-28
Help!

---

### Post by bFr-33 on 2010-10-29
Help!

---

### Post by Harry.HIrvola on 2010-12-27
sudo apt-get install libqt4-network;)

---

### Post by gsgleason on 2010-12-27
for future reference:
```
apt-file update
```
wait a while.
Then to find the package(s) that have said file, run this:
```
apt-file search filename
```

Example:
```
gsg@gregory:~$ apt-file search libQtNetwork.so.4
ia32-libs: /usr/lib32/libQtNetwork.so.4
ia32-libs: /usr/lib32/libQtNetwork.so.4.7
ia32-libs: /usr/lib32/libQtNetwork.so.4.7.0
libqt4-dbg: /usr/lib/debug/usr/lib/libQtNetwork.so.4.7.0
libqt4-network: /usr/lib/libQtNetwork.so.4
libqt4-network: /usr/lib/libQtNetwork.so.4.7
libqt4-network: /usr/lib/libQtNetwork.so.4.7.0
```

---

