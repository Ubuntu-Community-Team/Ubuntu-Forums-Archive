---
title: "Installing Packet Tracer error!"
date: 2012-01-10
forum: General Help
---

### Post by mohammedbakouban on 2012-01-10
Hi. 

I've downloaded Packet tracer 5.3 .bin and when I run it in Terminal to setup it says :

[PHP]mohammed@ubuntu:~$ '/home/mohammed/PacketTracer53_i386_installer-deb.bin' 
Self extracting archive...

gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
tar: Child returned status 1
tar: Error is not recoverable: exiting now
[/PHP]is it existing?? if so how do I open it!!
If not then how do I get rid of this?? 

thank you

---

### Post by satanselbow on 2012-01-10
try it like this:

```
./PacketTracer53_i386_installer-deb.bin
```

You might need to sudo it ;)

If that still fails re download the file from cisco as the messages rather imply the file may be corrupt.

---

### Post by prshah on 2012-01-10
> **mohammedbakouban said:**
> 
gzip: stdin: invalid compressed data--crc error
gzip: stdin: invalid compressed data--length error

Looks like the file is corrupt. "crc error" indicates the unpacked file does not match the original file.

Try redownloading the file, or use a different source if the error persists.

---

