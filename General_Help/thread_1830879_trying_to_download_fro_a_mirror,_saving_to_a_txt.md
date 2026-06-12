---
title: "trying to download fro a mirror, saving to a txt"
date: 2011-08-22
forum: General Help
---

### Post by Chrisian on 2011-08-22
hei, im trying to download zblock for my css server.
Im typing "wget http://zblock.mgamez.eu/files.htm?mirror=38"
but i only get a file named "files.htm?mirror=38"
im new to linux, what am i doing wrong?

help!

---

### Post by lisati on 2011-08-22
That file name looks like the name of a web page you'd visit to download the file rather than a link to the actual file.

I'd suggest looking inside the file to see if there's a downloadable link. One way of inspecting the contents of the file is this:
```
cat files.htm?mirror=38
```

---

### Post by Chrisian on 2011-08-22
this link "http://zblock.mgamez.eu/files.htm?mirror=38" is the link for downloading to windows, and iside the file it's just random signs.

---

### Post by raja.genupula on 2011-08-22
> **Chrisian said:**
> hei, im trying to download zblock for my css server.
Im typing "wget http://zblock.mgamez.eu/files.htm?mirror=38"
but i only get a file named "files.htm?mirror=38"
im new to linux, what am i doing wrong?

help!

other wise install flashgot plugin in firefox .in the tools look for "fashgot --> more options --> there set your default download manager as wget "

---

### Post by Chrisian on 2011-08-22
oh, i have a ubuntu server, non graph.

---

### Post by flemur13013 on 2011-08-22
I put that URL into FF and got a valid file named "zblock462.zip", using the default FF downloader.

Using wget, I got a file named "files.htm?mirror=38" which I could rename to whatever.zip and it opened OK. It'll look like random chars/junk if you cat or vi it.

---

### Post by Chrisian on 2011-08-22
> **flemur13013 said:**
> I put that URL into FF and got a valid file named "zblock462.zip", using the default FF downloader.

Using wget, I got a file named "files.htm?mirror=38" which I could rename to whatever.zip and it opened OK. It'll look like random chars/junk if you cat or vi it.

thank you so much!!

---

