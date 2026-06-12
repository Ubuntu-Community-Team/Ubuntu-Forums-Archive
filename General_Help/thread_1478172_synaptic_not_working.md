---
title: "synaptic not working"
date: 2010-05-09
forum: General Help
---

### Post by alegro on 2010-05-09
9.04 

I cannot download any packages via synaptic. I get "Failed to fetch" errors. I tried many different commands and other changes I saw on various threads. Now synaptic is only showing the already-installed packages. 

Is there a way to remove synaptic and reinstall it, aka start over?

---

### Post by howefield on 2010-05-09
You most likely won't need to reinstall synaptic.

Can you post the exact error that you are getting ?

---

### Post by alegro on 2010-05-09
I can only see the already-installed packages. If I can somehow see the not-installed packages, I can attempt to install one, and then get the error again, and post it here.

---

### Post by dino99 on 2010-05-09
on the left side can you select different lines on top, and filters on bottom ? at last, you can use the synaptic menu

---

### Post by alegro on 2010-05-09
```
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-X11-free/libqt3-mt_3.3.8-b-5ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/q/qt-X11-free/libqt3-mt_3.3.8-b-5ubuntu1_i386.deb)
 Could not resolve 'us.archive.ubuntu.com'


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/n/netgo/netgo_0.5-2ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/n/netgo/netgo_0.5-2ubuntu1_i386.deb)  
 Could not resolve 'us.archive.ubuntu.com'
```


[ netgo was the package I attempted to install]

---

### Post by stoneage on 2010-05-09
Those links work here. Possibly it is a problem with your internet connection.

Presumably you are having no trouble browsing. Did you try a different repository?

---

### Post by alegro on 2010-05-09
When I ran Firefox to check the network connection, I got no home page, and then I remembered I changed to a static IP address last night (see below). I changed back to DHCP and now synaptic works. Thanks guys. 

On an unrelated topic, I'm trying to connect 2 computers with a crossover cable (ethernet). Does anyone know a good complete tutorial? I haven't found one yet.

---

### Post by dino99 on 2010-05-09
you need to set your good settings into firefox prefs and network, check too your repo: need to be all "karmic" without "exotic" untrusted ones.
Better to use the main server, then update, upgrade

---

