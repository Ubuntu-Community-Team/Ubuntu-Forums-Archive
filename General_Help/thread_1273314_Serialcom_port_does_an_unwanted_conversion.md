---
title: "Serial/com port does an unwanted conversion"
date: 2009-09-23
forum: General Help
---

### Post by Jonas Arvidsson on 2009-09-23
I'm using Ubuntu 9.04 as the main platform for a project, using some of our external hardware. We are having a problem with that when the external hardware sends a "0x0D" (which in the case I found so far) is the checksum of a message, it is converted to "0x0A" when it reach the receiving program. Is there any way to turn such thing off?

---

### Post by StuartN on 2009-09-23
> **Jonas Arvidsson said:**
> Is there any way to turn such thing off?

Maybe check the settings with "stty -a" (see man stty), set the eol character and set onlcr off ("stty -onlcr").

---

### Post by Jonas Arvidsson on 2009-09-23
Only effect so far is that my terminal window get a pretty strange layout :)

---

### Post by StuartN on 2009-09-23
> **Jonas Arvidsson said:**
> Only effect so far is that my terminal window get a pretty strange layout :)

Yes, without any device argument it sets the terminal attributes - "stty onlcr" should restore it. You need to specify the device you are setting, such as "stty -F /dev/ttyS0 -a" lists attributes of the COM1 port.

---

### Post by Jonas Arvidsson on 2009-09-24
Ok! I'm very new to Linux. Only been working with MS for the last 15 years or so (except a few classes in OS like OpenVMS and AS/400 many years ago). Like it pretty much so far, but it feels like it is some sort of gap between what I need to ask, and my knowledge about it. 

What does "set the eol character" mean? I mean, I don't want any conversions at all, because we need to have the data from our external hardware just as it's sent. This is the only problem I noticed in this area so far, but I wouldn't be suprised if we might come across more problems if we can't be sure that the data received is the data sent.

---

### Post by StuartN on 2009-09-24
> **Jonas Arvidsson said:**
> What does "set the eol character" mean?

Choose the end-of-line character code(s). There is also end-of-file (eof), erase etc. These should not affect your output, but are worth checking. You set these character with a command like "stty eol ^L", but you could use eol 12 or eol 0xC for the same code. You go back to a safe setting with "stty sane" if everything gets really messed up.

The settings likely to affect your output are the output modifier settings like output carriage-return-to-newline (ocrnl) or output newline-to-carriage-return (onlcr). These are set on with "stty onlcr" and off with "stty -onlcr".

---

### Post by Jonas Arvidsson on 2009-09-24
Hm, you are writing "output" several times; Our problem is when external hardware sends to the computer. But the settings maybe work in both directions?

---

### Post by StuartN on 2009-09-24
> **Jonas Arvidsson said:**
> Hm, you are writing "output" several times; Our problem is when external hardware sends to the computer. But the settings maybe work in both directions?

Assuming that there are no similar translation taking place on the external hardware before transmission, then yes. "stty -icrnl" switches off carriag-return-to-newline conversion of the input data.

"stty -a" lists all the current settings. "man stty" lists all the available options.

---

### Post by Jonas Arvidsson on 2009-09-28
Much thanks for the help, now the problem is solved!

---

