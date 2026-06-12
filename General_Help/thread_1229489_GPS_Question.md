---
title: "GPS Question?"
date: 2009-08-02
forum: General Help
---

### Post by markytheone on 2009-08-02
Is there a package anywhere which will operate a GPS device via the command line?

I want to be able to run a command and have it return things like speed, lon & lat etc.

I have had a look at GPSdrive and a few others but they all seem to be for desktop versions with a GUI etc.

Any pointers would be great.

Thanks

Marky

---

### Post by markytheone on 2009-08-02
Any help?

---

### Post by dlmarti on 2009-08-02
It really depends on what you want to do with the data.

If you just want to see it coming in, there is always minicom.

If your looking for a gps interface, I would start looking at gpsd.

---

### Post by markytheone on 2009-08-02
All I need is a snapshot of the data at the time the command was run. Im going to create a script in PHP usig shell exec to put the data into a database on a remote server.

So I need a simply way or pulling data from the CLI.

Thanks

---

### Post by dlmarti on 2009-08-02
NMEA strings are already comma delineated, so I would just read directly from the serial port and skip the rest.

PHP can do this easily.

---

### Post by markytheone on 2009-08-02
Maybe im being stupid but can I still do that with a USB device? The GPS is connected via USB.

Thanks

---

### Post by dlmarti on 2009-08-02
> **markytheone said:**
> Maybe im being stupid but can I still do that with a USB device? The GPS is connected via USB.

Thanks

Unless the GPS is really strange (ie. one I don't know of), yes it will look just like a serial port.

---

