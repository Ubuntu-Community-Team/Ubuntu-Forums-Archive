---
title: "To Duplex or Not to Duplex"
date: 2010-09-23
forum: General Help
---

### Post by Special K on 2010-09-23
Apologies if this is not in the correct section, but a printer specific forum is not readily obvious.

I have turned over my main desktop PC to 10.04 after having used all previous releases of ubuntu on laptops.

If i connect my Canon ip4300 via usb, direct into my desktop, i can use pretty much all the functions of the printer. (the ones not available are a dpi greater than 600 and ink/cartridge monitor) but i can live without those.

It works perfectly with the full duplex (flip) function

However, i work from home and have a small network running. The children and wife still need access to the printer from their Microsoft machines. 

With this in mind, i set up an old low powered PC with XP, connected the printer and shared it on the network.

Everyone happy.....everyone except me!

I can see the printer over the network using Samba and can print to it....

The problem is, i now cannot use the duplex facility at all and its sooo frustrating.

Every time i send a print job from 10.04 to the printer, it spools and goes ok.

The problem then occurs....the XP machine kicks up an error, saying 

"a paper size that is not supported by the automatic duplex printing function is selected"

"stop printing, uncheck Automatic on the page setup tab of the printer driver, then print again"

This error appears on the XP machine....i cary out the advice in the error...and....nothing....the error keeps appearing and i cant print duplex.

Any advice greatly welcome

Steve

---

### Post by robsoles on 2010-09-25
I'd suggest re-connecting the printer to your Ubuntu 10.04 desktop machine and then looking into cups and samba to share it to windows users from there.

[www.google.com/search?q=share+ubuntu+printer+with+windows](www.google.com/search?q=share+ubuntu+printer+with+windows)
(see if you can find someone explaining to do it via GUI/Desktop before fiddling in terminal :))

---

