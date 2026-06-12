---
title: "Printing - SpliX Compression algorithm 0x0 does not exist"
date: 2010-08-20
forum: General Help
---

### Post by _ppr on 2010-08-20
Hello,

I have printer whhich work perfectly on ubuntu desktop
I shared it into network and trying to print from Mac
and I'm getting the following error:
"SpliX Compression algorithm 0x0 does not exist"

[IMG]http://dl.dropbox.com/u/1933399/1008/20098ktj0.png[/IMG]
Printer - Samsung SCX-4200

what can i do ?

---

### Post by lhamada on 2010-09-04
Hi,

I think you could:

1) Rebuild SpliX from current svn source, so that might have solved this.

2) Use the most updated package from ubuntu repository, from the next 10.10, ubuntu for example.

3) Setup a raw queue on cups on the server for this printer and install a native driver on the mac pointing to that queue. There is a SpliX for mac too: [http://guigo.us/mac/splix/](http://guigo.us/mac/splix/).

Good luck.

---

