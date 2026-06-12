---
title: "CUPS can't see parallel port printer"
date: 2009-12-21
forum: General Help
---

### Post by ExquisiteDeadGuy on 2009-12-21
I've been pulling my hair out trying to get this fixed since last night and have gotten nowhere.

If I try to add my parallel printer through CUPS, it doesn't give the option for a local parallel printer.

I can do echo 'test' > /dev/lp0 and it prints the test message. However CUPS refuses to see the printer. I've tried adding a printer manually with the URL of parallel:/dev/lp0 and I get the message:

"/usr/lib/cups/backend/parallel failed"

I've tried renaming the /etc/cups directory and reinstalling and it didn't help.

Doing lpinfo -v from the commandline gives

network lpd
network ipp
network http

If I go to "Add a printer" in the CUPS web menu it only shows:

LPD/LPR Host or Printer
Internet Printing Protocol (ipp)
Internet Printing Protocol (http) 

There's no option to add a parallel printer.

I went into BIOS and changed the parallel port mode to EPP and it didn't help.

Doing lsmod shows the parallel port module is loaded. I would GREATLY appreciate any help!

---

### Post by ExquisiteDeadGuy on 2009-12-21
I think this is related to the problem:

```
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/lpd (PID 1952)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/hp (PID 1953)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/scsi (PID 1954)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/serial (PID 1955)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/ipp (PID 1956)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/parallel (PID 1957)
D [21/Dec/2009:13:42:39 -0500] [CGI] list_devices_libusb
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/usb (PID 1958)
D [21/Dec/2009:13:42:39 -0500] [CGI] usb_find_busses=-2
D [21/Dec/2009:13:42:39 -0500] [CGI] usb_find_devices=0
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/snmp (PID 1959)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/hpfax (PID 1960)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/dnssd (PID 1961)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/http (PID 1962)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/beh (PID 1963)
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Started backend /usr/lib/cups/backend/socket (PID 1964)
D [21/Dec/2009:13:42:39 -0500] [CGI] Flushed attributes...
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Found device "lpd"...
D [21/Dec/2009:13:42:39 -0500] [CGI] Flushed attributes...
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Found device "ipp"...
D [21/Dec/2009:13:42:39 -0500] [CGI] Flushed attributes...
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] Found device "http"...
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1952 (lpd) exited with no errors.
E [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1953 (hp) stopped with status 13!
E [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1954 (scsi) stopped with status 13!
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1955 (serial) exited with no errors.
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1956 (ipp) exited with no errors.
E [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1957 (parallel) stopped with status 13!
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1958 (usb) exited with no errors.
E [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1960 (hpfax) stopped with status 13!
D [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1962 (http) exited with no errors.
E [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1963 (beh) stopped with status 13!
E [21/Dec/2009:13:42:39 -0500] [cups-deviced] PID 1964 (socket) stopped with status 13!

```

the Parallel back end is stopping with status 13. What is status 13 and how can I fix it? Googling uncovers nothing.

Thanks

---

### Post by ExquisiteDeadGuy on 2009-12-21
I'm able to print by using a second computer to print to a .ps file and then copying the .ps file to this computer and issuing:

cat file.ps > /dev/ps0

It prints everything, graphics and all, flawlessly. It just refuses to print through CUPS like normal.

Any ideas?

---

### Post by mackra on 2010-06-23
I'm having a similar problem.  Did you get your printer fixed?

---

