---
title: "ioctl with TIOCMGET on Prolific USB-RS232"
date: 2011-02-02
forum: General Help
---

### Post by KaibutsuX on 2011-02-02
In depth question here that probably isn't mainly Ubuntu related but wondering if anyone has any ideas.

I am running 10.04 64bit with all recent updates as of today.

About 1 month ago I copied the C file from [http://www.mvkonnik.info/2008/08/long-time-remote-shooting-with-canon.html](http://www.mvkonnik.info/2008/08/long-time-remote-shooting-with-canon.html) and compiled and tested it with my canon, prolific USB-RS232 converter. It worked great and I started designing an application built with GTK+ to make a little automated program.

Anyway as I'm implementing the shutter controls today, I can't get my implementation to work, so I go back to the original, compile and all of a sudden it's not working either.

I've done quite  a bit of debugging and here is everything I know:

My prolific adapter is installed as shown in lsusb
dmesg shows that is mapped as /dev/ttyUSB0
A simple loopback test from jumping pins 2 and 3 confirms that the connection is valid.
After GDB'ing the original C program I find that the ioctl call using TIOCMGET or TIOCMSET are failing with a return code of -1 and strerror(errno) of "Invalid argument".
So then I install statserial which I run and gives: statserial: TIOCMGET failed: Invalid Argument

I found an article (just a single one) saying that TIOCMGET was deprecated but I seriously doubt that an ubuntu update broke this is a LTS version so I can't figure out why my ioctl call is failing.

Anyone have any ideas or other debugging hints?

---

