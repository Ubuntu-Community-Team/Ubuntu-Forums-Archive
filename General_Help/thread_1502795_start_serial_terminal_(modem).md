---
title: "start serial terminal (modem)"
date: 2010-06-06
forum: General Help
---

### Post by LeServal on 2010-06-06
Dear forum members,

I would like to enable on 10.04 a terminal on ttyACM0 (my modem);
I would like to first enable autoanswering in the modem with
cu -l ttyACM0, then ATS0=1, then exit cu, THEN start the serial
terminal.

This has worked in the past in event.d, now I see /etc/init;
I tried copying tty3.conf and just renaming the terminal, but
that did not work, the screen remained black and blank.

For testing, I tried copying tty3.conf to tty9.conf and starting
tty9 while Ubuntu Lucid is running with kill -1 1, did not work.
If tty9 would work, I would know that in principle, creating a
terminal on ttyACM0 should be possible. - If I restart the
machine with tty9.conf, it creates the terminal nicely; but for
the modem terminal it is necessary that the modem's state is
preserved, and that is why a restart of the machine is out of
question.

Therefore, I would like to kindly ask to first be told how to
start tty9 without restarting Ubuntu, as well as stopping it
without shutting down, and then, if the test result is positive,
I would like to ask how to define the terminal ttyACM0.

Remark: I had it working in 8.04 and NetBSD, so generally, it
should be possible with my hardware. The final goal is a dial-in
server.

Thank you in advance for your very obliging help.

---

### Post by LeServal on 2010-06-17
OK, I figured out how to create a dial-in server. In fact, you just need to install mgetty and then to adjust /etc/mgetty/mgetty.config and to create /etc/init/ttyACM0 (I assume the modem is on ttyACM0 - could be instead ttyUSB0 or even ttyS0) with the appropriate contents. The following gives you a setup at 300 baud that picks up the call after one ring; it proved quite nice if you want to use an acoustic coupler to connect (as I indeed did):

/etc/mgetty/mgetty.config:

port ttyACM0
  init-chat "" \d\d\d+++\d\d\dATZ OK ATX0L3&D0&C1S37=1S10=255S7=45 OK
  answer-chat "" ATA CONNECT \c \r
  debug 9
  data-only y



/etc/init/ttyACM0.conf:

start on runlevel [23]
stop on runlevel [!23]

respawn
exec /sbin/mgetty -D -s 300 -n 1 ttyACM0

Then reboot. - You should try yourself whether all Hayes-commands would work on your modem, e.g. giving them individually using the program "cu". I sometimes got ERROR for ATS37=1 (on a cellphone) as well as for ATS10=255, but leaving those out was no problem. - A little remark: If you use your cellphone as a modem, you can log in only with another cellphone, but not with a true analog modem. (The reason is that the cellphone will not recognise other calls as data-calls and will thus not give you a terminal.) The other way round - i.e. terminal on an analog modem, you try to log in over cellphone - works fine, as the analog modem makes no differentiation between voice call and data call. Another remark: do NOT set mgetty to do ATS0=1 (i.e. autoanswer as Hayes-command) as that will spoil it, actually, as mgetty expects to pick up the call itself (that is the "-n 1"-part I mentioned).

Good luck.

---

