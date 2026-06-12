---
title: "having problems with  Windows workgroup networked printer/scanner"
date: 2011-10-23
forum: General Help
---

### Post by huggs on 2011-10-23
I have my Ubuntu machine connected to my LAN which is hosted by Windows Vista computer. On the network, there is a Canon MX300 printer/scanner, which prints fine for me using the Canon MP150 driver, since there's no driver for the MX300.

The printer's address in System/Administration/Printing/Properties(of the printer) is
smb://WORKGROUP/TOM-PC/Canon%20MX300%20series%20Printer

Like I said, it prints fine.

I tried using Simple Scan, and it detects no scanner.
So I installed xSane, made sure I had the sane backend, and xSane searches for a scanner when I open it, but finds none.

What do I need to do in order to get this thing to scan? It scans fine on the Vista machine that it is connected to via usb, and on the Windows 2000 machine that is also connected to the LAN. Just no joy from my Ubuntu box.

I read somewhere that since it's on the network, I'd have to edit /etc/sane.d/pixma.conf and put the scanner's uri in that file.
I do not know the scanner's uri, or how to find out what it is. Google is being very tight-lipped about this little secret.
All I know is that it's supposed to begin with bjnp://

Can somebody please shed some light for me, I've been wandering around in the dark for hours...                    Thanks guys  :D

---

### Post by oldtimer7777 on 2011-10-23
I had the same problem. I bought a network printer adapter and plugged my printer directly into the router switch.  That fixed it. Ubuntu could see it and I could install the driver for it on any OS too.

> **huggs said:**
> I have my Ubuntu machine connected to my LAN which is hosted by Windows Vista computer. On the network, there is a Canon MX300 printer/scanner, which prints fine for me using the Canon MP150 driver, since there's no driver for the MX300.

The printer's address in System/Administration/Printing/Properties(of the printer) is
smb://WORKGROUP/TOM-PC/Canon%20MX300%20series%20Printer

Like I said, it prints fine.

I tried using Simple Scan, and it detects no scanner.
So I installed xSane, made sure I had the sane backend, and xSane searches for a scanner when I open it, but finds none.

What do I need to do in order to get this thing to scan? It scans fine on the Vista machine that it is connected to via usb, and on the Windows 2000 machine that is also connected to the LAN. Just no joy from my Ubuntu box.

I read somewhere that since it's on the network, I'd have to edit /etc/sane.d/pixma.conf and put the scanner's uri in that file.
I do not know the scanner's uri, or how to find out what it is. Google is being very tight-lipped about this little secret.
All I know is that it's supposed to begin with bjnp://

Can somebody please shed some light for me, I've been wandering around in the dark for hours...                    Thanks guys  :D

---

### Post by huggs on 2011-10-23
Ok, thanks. Guess I'm off to Wal-Mart. :)

---

### Post by oldtimer7777 on 2011-10-23
> **huggs said:**
> Ok, thanks. Guess I'm off to Wal-Mart. :)

i bought my usb to ethernet adaptor from Fry's Electronics for 16.99 us dollars.

---

