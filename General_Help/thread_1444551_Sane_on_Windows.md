---
title: "Sane on Windows"
date: 2010-04-01
forum: General Help
---

### Post by mk1w86 on 2010-04-01
Is it possible to install the sane-backends package on Windows?  

I need to do this so I can share a scanner connected to a Windows machine across the network for Windows and Linux clients running Xsane.

---

### Post by Chesamo on 2010-04-01
It seems possible, but not easy. And there's only SCSI support, so.... yep :(

[http://www.zago.net/sane/windows/sane_on_windows.html](http://www.zago.net/sane/windows/sane_on_windows.html)

Theoretically it should be possible to compile the SANE backend on Windows... try reading README.windows in the source tarball.

Quick question: Why can't you connect the printer to a Linux host and use a SANE frontend (of which there are a few for Windows) instead?

---

### Post by mk1w86 on 2010-04-01
I have actually already seen the link that you have posted from googleing and I was going to try that but I asked here first to see if there was an easier way.  It is a SCSI scanner so there should be no problems there. :D

> Quick question: Why can't you connect the printer to a Linux host and use a SANE frontend (of which there are a few for Windows) instead?

The scanner is currently set up on a Debian machine and works fine with sane shared across the network, I use Xsane  as the frontend on Linux and Windows.  The reason for wanting to run sane-backends on Windows is that I also have a printer (Epson R300) shared across the network on another machine that is running Windows, it runs Windows because I have never been able to set cups up correctly to print on CD's.  This means I have to have two machines running, a print server and a scan server.  I was hoping to connect the printer and scanner to the same machine so I would only have to have one running. ;)

---

### Post by Chesamo on 2010-04-01
> **mk1w86 said:**
> The scanner is currently set up on a Debian machine and works fine with sane shared across the network, I use Xsane  as the frontend on Linux and Windows.  The reason for wanting to run sane-backends on Windows is that I also have a printer (Epson R300) shared across the network on another machine that is running Windows, it runs Windows because I have never been able to set cups up correctly to print on CD's.  This means I have to have two machines running, a print server and a scan server.  I was hoping to connect the printer and scanner to the same machine so I would only have to have one running. ;)
Ah, understandable.

---

