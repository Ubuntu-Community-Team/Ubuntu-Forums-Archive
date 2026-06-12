---
title: "Help with Chaintech AV710"
date: 2006-04-22
forum: General Help
---

### Post by spm on 2006-04-22
I bought this card because I had read it was easy to setup in Ubuntu.

Well no luck so far on 5.10.

Stupid question, if doesnt show up in **lspci**...is it not inserted properly then?

doing modprobe snd-ice1724 does not give error, but also is not loaded when rebooting.

UPDATE:

Got it...not sure if the card was not sitting right, I reset it...and I also added the **snd-ice1724 **to **/etc/modules**. One of them got it to work!

---

