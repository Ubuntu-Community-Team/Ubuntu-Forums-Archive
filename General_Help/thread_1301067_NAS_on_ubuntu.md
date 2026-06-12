---
title: "NAS on ubuntu"
date: 2009-10-25
forum: General Help
---

### Post by FreezWay on 2009-10-25
in my house we have:
2 ubuntu desktops (mine and my dads)
1 windows vista computer
2 xp computers (netbook and ancient PIII)
1 even older macintosh power PCC barely running tiger

My dad sent me on a quest to find out how to set up a NAS on his ubuntu computer (celeron @ 2.66GHz (dual core), 512 MB ram) that all the computers in the house could access. he plans to add 2 500GB HDD's in raid redundant. how might one go about this?

---

### Post by earthpigg on 2009-10-25
do you really have your heart set on using a ***new*** computer for this?

im eyeing that ancient P3 and thinking [FreeNAS]("http://en.wikipedia.org/wiki/Freenas")

once it's set up, you can strip the P3 FreeNAS machine's keyboard, mouse, and monitor and run it 'headless' using the web interface for FreeNAS from any other computer.

then, i'd put the extra monitor you now have on whichever of the two ubuntu machines has an NVidia card (just because nvidia's app makes it easy to set up dual display).

and keep the keyboard/mouse wherever you lounge with the netbook most often.

---

### Post by P4man on 2009-10-25
Honestly, consider buying a dedicated NAS box. They are cheap, and then you can power the computer(s) off. Having a PC run 24/7 to serve as NAS for 2 drives, the electricity bill will quickly repay the NAS.

---

