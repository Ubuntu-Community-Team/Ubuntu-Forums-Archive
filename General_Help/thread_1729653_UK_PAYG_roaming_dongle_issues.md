---
title: "UK PAYG roaming dongle issues?"
date: 2011-04-15
forum: General Help
---

### Post by Shenachie on 2011-04-15
Carphone Warehouse has just told my better half that there is not one dongle that can now be used with Linux.

Can this possibly be true?

Shenachie

---

### Post by mendhak on 2011-04-15
What they likely mean is that it isn't supported, so if there are problems, they will not tell her how to fix it as they don't know.

I've seen posts on how to get dongles working on Ubuntu, but it may not be as straightforward as plugging it in and off you go (sometimes it is).  I suggest you find out the model number of the dongle you want and then do a search for it with ubuntu.  You may have to do a bit of fiddling to get it working in some cases.

Fiddly example: 
[http://stanford-clark.com/3dongle.html](http://stanford-clark.com/3dongle.html)

Straightforward example:
[http://www.technicalathma.com/2010/09/installing-3g-dongle-on-ubuntu/](http://www.technicalathma.com/2010/09/installing-3g-dongle-on-ubuntu/)

---

### Post by tredegar on 2011-04-15
> Can this possibly be true?
No, I have a Huawei E620 (USB ID 12d1:1001) which works "out of the Box" with 10.04.

I got it from "3".

For a list of others that are likely to work try take a look in **/etc/usb_modeswitch.d/**

But what I did was to take my little EEE701 running linux into the shop and try different dongles. The first one worked though. You'll need "Network Manager" and not **wicd** if you like a GUI to set up your connection.

---

### Post by jimmers on 2011-04-15
Hi,
I am using a Huawei K3565, from Vodafone it has worked straight out of the box since Jaunty, I am using it now as I type this reply, but as has been said before, check for compatability before purchasing, if you decide on Vodafone, Google "Vodafone Mobile Connect", or go to [www.betavine.net/bvportal/resources/datacards](www.betavine.net/bvportal/resources/datacards).

I do not know if it is still the same but when I ran a 3 dongle, if I did not use all the bandwith that I had payed for, within 30days I lost it, with Vodafone it is 180 days, or it was the last time I checked.

Whether this is useful to you or not, I don't know, but it just my two p's worth.

Luck with what ever you choose.

---

### Post by tilii on 2011-04-15
Hi,

I am currently using a ZTE MF112 from 3. No issues. It has a slot for Micro SD cards which is also useful. When plugged in it is first recognised as a drive (on my system at least) so you just need to "eject" it for the modem part to kick in.

---

