---
title: "communicating over serial port with minicom"
date: 2009-12-20
forum: General Help
---

### Post by Leporello on 2009-12-20
Hi,

I have a machine with 2 serial ports. I would like to send a message (e.g. one or more ascii characters) from one serial port to the other. (Ultimately, I'm trying to write a program to communicate with a hardware device over serial interface. Since I know next to nothing about serial programming, this seemed like a reasonable place to start). I read about a program called minicom and it sounded like it might fit the bill. My idea is to create two instances of minicom, one attached to serial port 1 (/dev/ttyS0) and the other attached to serial port 2 (/dev/ttyS1). I would like to be able to just type in one terminal and have whatever I'm typing show up in the other one. But I can't seem to figure out how to do this - none of the options (send file, etc) seem appropriate, and google isn't much help either, most everything I find talks about how to set up minicom, not how to actually use it! And no matter what I do, the minicom window always says "offline". Can anyone provide some guidance on this? Is this even a reasonable thing to try to do? Thanks!

---

### Post by iponeverything on 2009-12-20
It sounds like a fun project. It is every strait forward.

Do a google search on:

"serial communication tutorial"

---

