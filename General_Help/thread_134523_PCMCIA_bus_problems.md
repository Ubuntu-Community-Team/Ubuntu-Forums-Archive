---
title: "PCMCIA bus problems???"
date: 2006-02-22
forum: General Help
---

### Post by Kreakboy on 2006-02-22
Howdy all,

I have an old Toshiba Satellite 4100XDVD laptop running Ubuntu Breezy Badger 5.10 and I'm trying to get my Belkin Wireless G PCMCIA network card (Part # F5D7010) to work on it. 

I've worked out its running the RaLink Chipset that supposed to run straight outta the box on Ubuntu 5.10, but mine never seems to work.

I've checked out divice manager and this is what comes up when its inserted into the top PCMCIA slot.
[IMG]http://users.tpg.com.au/asgrixti/photo's/Screenshot.jpg[/IMG]
as you can see it's showing up, but in networking doesnt show up.

And when I iwconfig in terminal this comes up.
[IMG]http://users.tpg.com.au/asgrixti/photo's/Screenshot1.jpg[/IMG]
I far as i know when the card is in the slot, ra0, should also be in the list.

Im not exactly sure whats going on, but my farther seems to think the motherboard is the problem, while i think its the PCMCIA bus. Has anyone else had this problem, if so, how did you fix it?? Or does anyone have any ideas on how to fix it without spending $$$


Cheers in Advance,
Kreakboy

---

### Post by Kreakboy on 2006-02-24
Any help please? I have no idea whats going on!
Cheers,
Kreakboy

---

### Post by stuart.crouch on 2006-02-24
It looks like you have a couple of options.  I couldnt find a site that says where you get it working "out of the box", but this site suggests that you can use the windows ndiswrapper and the open source drivers once you've installed and compiled them.

[http://www.leenooks.com/72](http://www.leenooks.com/72)

On the plus side, your pc detects the device and ndiswrapper option is easy using the ndisgtk - [http://spohlenz.blogspot.com/2005/07/everyone-likes-screenshots.html](http://spohlenz.blogspot.com/2005/07/everyone-likes-screenshots.html)

Its in one of the repositories - I got it by searching for ndisgtk in synaptic.

Trying the above methods wont cost $$$ at least and will confirm its something you have to do to your distro rather than a problem with the hardware.

---

