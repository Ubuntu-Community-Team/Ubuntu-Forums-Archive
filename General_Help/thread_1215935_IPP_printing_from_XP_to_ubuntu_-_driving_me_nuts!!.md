---
title: "IPP printing from XP to ubuntu - driving me nuts!!"
date: 2009-07-17
forum: General Help
---

### Post by neill on 2009-07-17
Hi

I have an ubuntu 8.10 machine with an HP deskjet attached

This works fine to print from locally

With other linux clients i print over the LAN using ipp:\\serverIP:631\printers\deskjet to install the printer - works fine too

With XP I can *install* the printer using http:\\serverIP:631\printers\deskjet but it won't actually print :confused:

However from the exact same XP client if i go to \\serverIP:631 I can print test pages perfectly from the CUPS web interface :cry:

Clearly something screwy about the way XP implements IPP

Anyone any ideas (I've seen a few forum posts elsewhere with the same prob, but no solutions!!)

Ta

/neill

---

### Post by neill on 2009-07-17
and i get a 'client-error-document-format-not-supported' in the CUPS logs !

---

### Post by neill on 2009-07-17
answer is here

[http://mindspill.net/computing/cross-platform-notes/cups-client-error-document-format-not-supported.html](http://mindspill.net/computing/cross-platform-notes/cups-client-error-document-format-not-supported.html)

:P

---

