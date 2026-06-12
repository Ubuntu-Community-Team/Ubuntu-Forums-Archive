---
title: "ser2net issue"
date: 2009-08-16
forum: General Help
---

### Post by redscorpion69 on 2009-08-16
Sorry if this is posted in a wrong forum.

I am trying to pipe tcp connection with ser2net to connect to a cisco switch console port, using prolific usb to serial232 cable. Actually 4 cables, for 4 switches.

sudo tail -f /var/log/messages  shows that USB0,1,2,3 is connected so no need for drivers.

in /etc/ser2net.conf i typed

2011:telnet:600:/dev/ttyUSB0:9600 8DATABITS NONE 1STOPBIT banner
2012:telnet:600:/dev/ttyUSB1:9600 8DATABITS NONE 1STOPBIT banner
2013:telnet:600:/dev/ttyUSB2:9600 8DATABITS NONE 1STOPBIT banner
2014:telnet:600:/dev/ttyUSB3:9600 8DATABITS NONE 1STOPBIT banner

then i run 'ser2net' in terminal.
now when i telnet, telnet localhost 2011 :

Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

ser2net port 2011 device /dev/ttyUSB0 [9600 N81] (Debian GNU/Linux).


So what's next? What part am i missing? I am not acquainted with Ubuntu very well :)

---

### Post by redscorpion69 on 2009-08-17
Still no progress.
Anyone?

:(

---

