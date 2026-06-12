---
title: "Drivers problem, blank desktop"
date: 2010-03-24
forum: General Help
---

### Post by Cokaric on 2010-03-24
I have graphic card Radeon 9000 Series. I installed Ubuntu 8.10 yesterday, I upgraded system 2 times till now. I am on Ubuntu 9.10 right now, well this morning I was on 9.04 but I decided to upgrade again. Everything was running smoothly till I upgraded to 9.10. After restart desktop gone blank, no icons or desktop background and everything was running slow. So after 2 hours of playing with commands I decided to lower my resolution. Now everything is working fast like when I first installed Ubuntu, but on lower resolution. On Ubuntu 8.10 and 9.4 everything was running fast on highest resolution, but now it doesn't ?

Some explanation or help how to fix this. If no1 knows 1152 * 864 isn't bad resolution, and I can get used to it.

Anyway, gr8 OS guys, plz continue developing && supporting it ;P


Best regards,
Cokaric

---

### Post by Mark Phelps on 2010-03-25
There is no ATI restricted driver that will support your card in Ubuntu 9.04 or newer.  

If you accidentally forced the install of one, and them removed it, replacing it with the open source drivers, those are the only drivers that will work now.

You use the Display applet in the Settings menu to establish or change resolutions now since 9.10 doesn't actually need an xorg.conf file anymore.

---

