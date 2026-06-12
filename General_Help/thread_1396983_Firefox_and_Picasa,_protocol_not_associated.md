---
title: "Firefox and Picasa, protocol not associated"
date: 2010-02-02
forum: General Help
---

### Post by LK_gandalf_ on 2010-02-02
Hi all. I installed Picasa and if I try to download an album it says that the protocol picasa is not associated with any application.

I followed this instructions ([https://support.mozilla.com/en-US/kb/The+protocol+is+not+associated+with+any+program](https://support.mozilla.com/en-US/kb/The+protocol+is+not+associated+with+any+program)) and I added the following settings in about:config:

network.protocol-handler.app.picasa;/opt/picasa/bin/picasa
network.protocol-handler.external.picasa;true

But nothing changed.
I'm using Kubuntu 9.10 and firefox from repository. Picasa is downloaded and installed from the .deb from the official website.

Do oyu have any sugegstion to fix it?
Thanks

---

### Post by lovinglinux on 2010-02-02
Open about:config, then type **network.protocol-handler** in the filter form, then then create a new **true** boolean entry for **network.protocol-handler.expose.picasa**.

Try again. If that doesn't work, then right-click in the **network.protocol-handler.app.picasa** and select the **Reset** option.

The explanation why it is not working is in the [Caveats section of the network.protocol-handler.external.(protocol) page on kb.mozillazine.org](http://kb.mozillazine.org/Network.protocol-handler.external.%28protocol%29#Caveats).

---

### Post by LK_gandalf_ on 2010-02-13
unfortunately it doesn't work :( anyone solved this issue?

---

### Post by LK_gandalf_ on 2010-03-02
anyone succeded?

---

### Post by barna on 2010-11-15
I am still having this problem, in 2010, ubuntu 10.04. It sometimes works, though, and then suddently I can't download albums anymore. 
Still no solution to this problem?

Does anybody know, what is the link picasa://???? for a given album? It would be much easier to launch 
picasa command_to_download_the_given_album
from the command line, rather than spending several hours with this **** problem, still without a solution. The HTML source code of the picasa web albums is unfortunately not really human-readable, I could not find the given picasa:// link in it.
Thanks

---

### Post by barna on 2010-11-15
[http://googlesystem.blogspot.com/2007/12/download-picasa-web-albums-without.html](http://googlesystem.blogspot.com/2007/12/download-picasa-web-albums-without.html)

---

