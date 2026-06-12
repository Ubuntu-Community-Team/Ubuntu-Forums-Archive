---
title: "Visual system load indicator for no gui server"
date: 2010-01-31
forum: General Help
---

### Post by t4thfavor on 2010-01-31
I am on the hunt for some kind of device that I can hookup to a few of my servers, and then see at a glance what the system load is at that moment.

It could be as simple as 4-5 LED's that light as the load gets higher.

I am a developer, so I am not opposed to using a microcontroller if anyone can point me at any that have good Linux support (for programming them as well).

I have a Dell XPS as my "server" which has a rather annoying multi-color LED in the front, I would probably just want to figure out how to "drive" that one as it has a perfect array of colors to tell me load.


I have tried the SMBios dellLEDctl app, but it tells me that it has no support on this system.

This leads me to believe I am going to need some other kind of controller to plug in via serial, or usb. 

Any Ideas?

---

### Post by undecim on 2010-01-31
Perhaps a small LCD? (like on a watch, not a laptop)

A Google search shows [http://www.crystalfontz.com](http://www.crystalfontz.com) to be a promising place to find them. Under the "software" page they have a download with C program examples to control the displays.

---

### Post by t4thfavor on 2010-01-31
Small LCD would be great, but not readable at a glance or from across the room. I could go with the model that has 4 LED's to the left side, but that seems overkill if you just want to read load at a glance.

I guess I am more looking for a cheap microcontroller chip, that has good linux support, and only a few IO ports.

Something like the PICAxe chip, but less Windows Only.

---

