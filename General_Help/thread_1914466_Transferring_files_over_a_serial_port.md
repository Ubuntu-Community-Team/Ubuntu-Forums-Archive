---
title: "Transferring files over a serial port"
date: 2012-01-24
forum: General Help
---

### Post by outleradam on 2012-01-24
I'm porting ubuntu to a new device. It is an embedded device. I've got the bulk of ubuntu onto my device already, but i'd like to make hot-system configuration changes. Can 'dd' handle this? Will this idea work? 
 
I have a serial connection with a root shell on my new device. I can execute ```
dd of=/home/user/myfile
``` Which should write to a file from STDIN?
 
Then on my Ubuntu desktop I should be able to execute ```
cat myfile >/dev/ttyUSB0
``` which should port STDOUT to the serial port and thereby write the file.
 
I'm not near my setup right now, but this thought occurred to me and I'd like to know: is this possible? How can I reduce errors in the transfer?

---

### Post by Slim Odds on 2012-01-24
> **outleradam said:**
> I'm porting ubuntu to a new device. It is an embedded device. I've got the bulk of ubuntu onto my device already, but i'd like to make hot-system configuration changes. Can 'dd' handle this? Will this idea work? 
 
I have a serial connection with a root shell on my new device. I can execute ```
dd of=/home/user/myfile
``` Which should write to a file from STDIN?
 
Then on my Ubuntu desktop I should be able to execute ```
cat myfile >/dev/ttyUSB0
``` which should port STDOUT to the serial port and thereby write the file.
 
I'm not near my setup right now, but this thought occurred to me and I'd like to know: is this possible? How can I reduce errors in the transfer?

You need to use something like minicom or else encapsulate the serial data with something like TCP/IP (ppp [https://en.wikipedia.org/wiki/Point-to-point_protocol](https://en.wikipedia.org/wiki/Point-to-point_protocol))

---

### Post by outleradam on 2012-01-24
> **Slim Odds said:**
> You need to use something like minicom or else encapsulate the serial data with something like TCP/IP (ppp [https://en.wikipedia.org/wiki/Point-to-point_protocol](https://en.wikipedia.org/wiki/Point-to-point_protocol))
 to do what?  I asked 3 questions.

---

### Post by outleradam on 2012-01-24
How will minicom help and in what way?  I'm using a serial console not a modem connection.

---

### Post by 1clue on 2012-01-24
A modem is just a hardware transfer medium.  If you're using a serial to serial connection, then you're using a null-modem cable in the middle.

Minicom handles all the extra junk involved.  You have a serial port, but you need to tell the other side you're about to transfer files, what the file is to be called and all that.  It also uses protocols which help reduce errors.

Minicom is designed for situations like the one you're describing.  The other alternative is to set up an sftp server on it (requires tcp/ip) or a small webmin-style web server on it (also requires tcp/ip)

---

### Post by dcstar on 2012-01-25
> **outleradam said:**
> 
........
I'm not near my setup right now, but this thought occurred to me and I'd like to know: is this possible? How can I reduce errors in the transfer?

```
man uucp
```

---

### Post by Slim Odds on 2012-01-26
> **outleradam said:**
> to do what?  I asked 3 questions.

You asked 5 questions. Maybe you should number them next time.

That was the answer to all 5 questions.

---

### Post by ottosykora on 2012-01-27
I recall using similar procedure on a small industrial embeded computer.

Under linux writing the the serial port as device is the common thing and should work.

However I remember we had to take care first of the serial not wanting to use any handshakes etc to make things simpler.

On other side I was just reading it with hypertherm.

So in your case you will more have to take care what should happen on the other side with the data arriving at the serial port.

---

