---
title: "Ubuntu 9.10 x86_64 printing issue"
date: 2010-01-01
forum: General Help
---

### Post by louix on 2010-01-01
Hi
My mother has a desktop PC with Ubuntu 9.10 x86_64.
At this time no application can find my mothers printer which is a Canon i560. It has worked fine previously.
When I go to System > Administration > Printing nothing happens. If I run the application in a terminal I get this output: [http://pastebin.com/fcba6a3](http://pastebin.com/fcba6a3)
If I try to update the system in a terminal I get this output: [http://pastebin.com/f40a54132](http://pastebin.com/f40a54132)
I've also tried to use the Synaptic tool "Fix broken packages" but it can't fix it.
My mothers desktop used to have some RAM errors. I think that this problem may have been caused by a system crash caused by defective RAM while the machine was doing a system update. She  has got some new RAM, that works fine.
Anybody that can help me fix this problem? :)

---

### Post by louix on 2010-01-02
I've solved this problem.
I did these to things:

1.
Deleted the folder /usr/lib/python2.6 og copied the folder from a well-functioning installation.

2. Re-link
sudo rm /usr/bin/python
cd /usr/lib/
sudo ln -s python2.6 /usr/bin/python

If you have the same problem, then first try #2 and if it don't solv your problem then try #1

---

