---
title: "Serial port on another computer (sharing?)"
date: 2011-08-22
forum: General Help
---

### Post by Cool Javelin on 2011-08-22
I have a need to displace a serial port from one Linux computer to another computer running Windows (XP.)

I am running Heyu on a Linux machine in a closet. The power leg for that circuit cannot let the X10 communication reach most of the rest of the house.

Where it does work, is from my office but there I am running XP computers only.

I would like to plug the CM11A into my XP computer, share it's serial port and have the home automation computer (running Heyu and Linux) use the LAN to get to the XP serial port without Heyu knowing it is not a local port.

Has anyone done this? Can I share a serial port in XP? Can I get Linux to map a serial port to a virtual one on another machine?

Thanks for any help,
Mark.

P.S., before you ask, I have many other hardwired signals from various places in the house already wired into the closet so moving the home automation computer to another local can't be done.

---

### Post by tredegar on 2011-08-22
> I have a need to displace a serial port from one Linux computer to another computer running Windows (XP.)

Your problem involves windows, which I do not use.

But for transferring ports, and communications, between computers **netcat** is very, _very_ good.

Search on it.

Good luck.

---

