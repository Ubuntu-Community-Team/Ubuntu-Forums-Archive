---
title: "Create a Windows rescue disk"
date: 2009-07-07
forum: General Help
---

### Post by deviant78 on 2009-07-07
I am trying to create a rescue disk for windows on a Ubuntu bootable USB stick.

I'll be doing this from a live cd, I want to include a virus scanner and a spyware scanner which can be run from the USB disc on a mounted faulty windows drive.

I'd also like to create a file with a list of usefull commands, such as the linux equivelent to fixmbr.

Can anyone please help with this?

---

### Post by sedawk on 2009-07-07
"Replacement" for fixmbr:

[http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/)

Virus Scanner working on Ubuntu: clamav

I'm not aware of a native anti-spyware tool for linux,
but Spybot S&D runs under Wine since 1.5.

There are many windows problems you cannot fix from
a bootable Ubuntu stick. You very often need to run the damaged
windows and install some additional tools to repair or check
the system (like the sysinternals suite) from inside.

---

