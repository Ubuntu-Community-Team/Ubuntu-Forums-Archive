---
title: "Block a server completely?"
date: 2011-03-27
forum: General Help
---

### Post by evenrelation on 2011-03-27
Is it possible to block a server completely from any connectivity to my Ubuntu system so that not even Google Search will detect files from that server?

The server in question is <http://fir.nes.ru>.

This is because of a nightmare issue I have been having with the Firefox Addon "DownThemAll!" which, I won't go further into.

---

### Post by fela on 2011-03-27
```
gksudo gedit /etc/hosts
```

Put at the end of the file, as a new line:

127.0.0.1 fir.nes.ru

Save and close the file.

EDIT: if google hosts files from that server (which I highly doubt) then you can't block that unless you want to block google. If google simply links to the server, then when you click the links it will say something like 'couldn't connect to server' or something similar.

---

### Post by evenrelation on 2011-03-27
Great, thanks.

---

