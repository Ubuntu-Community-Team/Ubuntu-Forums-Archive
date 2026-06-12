---
title: "Starting soundmodem (err:  No Channels Configured&quot;"
date: 2012-01-16
forum: General Help
---

### Post by Larrie07 on 2012-01-16
I am trying to run xastir with a signalink USB interface.  I followed the information in an earlier thread on Sound card interfacing.  I ran soundmodemconfig, set up a new configuratgion called SM0, set up a channel 0, and verified in the diagnostics menu that it was working.  In the scope mode, I could see the signals and in the terminal the APRS packets were being decoded correctly.  Even the PTT worked correctly.

When I run sudo soundmodem, I get the error message "No Channels Selected".  I tried the command soundmodem start, but I get the error message:
I/O warning : failed to load external entity "start"
sm[4602]: Error parsing config file "start"

I have started xastir and tried several port configuations but all produce the error "no active ax25 port".

What am I missing?  I am new to linux, so I need basic instructions.

---

### Post by kd5mkv on 2012-08-01
Try the xastir wiki!
[http://www.xastir.org/wiki/HowTo:SoundModem](http://www.xastir.org/wiki/HowTo:SoundModem)

There is probably a gui version around maybe in the repository. I used this
program once on windows  with flexnet packet radio.

---

### Post by apomm84 on 2013-03-26
Hello
have you solved your problem, if I can help you

---

