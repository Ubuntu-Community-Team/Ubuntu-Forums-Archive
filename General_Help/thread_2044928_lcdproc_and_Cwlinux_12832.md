---
title: "lcdproc and Cwlinux 12832"
date: 2012-08-20
forum: General Help
---

### Post by Statia on 2012-08-20
When I couldn't get lirc to work, I decided I'd give the serial port another destination, so I got a Cwlinux 12832 LCD. Using the documentation here

[http://lcdproc.sourceforge.net/docs/current-user.html#CwLnx-howto](http://lcdproc.sourceforge.net/docs/current-user.html#CwLnx-howto)

I get all the software running.
This is what shows in syslog:

```
08/20/12 03:25:08 PM    quokka  LCDd    LCDd version 0.5.5 starting
08/20/12 03:25:08 PM    quokka  LCDd    Built on Feb 27 2012, protocol
version 0.3, API version 0.5
08/20/12 03:25:08 PM    quokka  LCDd    Using Configuration File: /etc/LCDd.conf
08/20/12 03:25:08 PM    quokka  LCDd    Set report level to 4, output to syslog
08/20/12 03:25:08 PM    quokka  LCDd    Server running in foreground
08/20/12 03:25:08 PM    quokka  LCDd    Listening for queries on localhost:13666
08/20/12 03:25:08 PM    quokka  LCDd    CwLnx: using Device /dev/ttyS0
08/20/12 03:25:08 PM    quokka  LCDd    CwLnx: Config tells us we have a keypad
08/20/12 03:25:08 PM    quokka  LCDd    CwLnx: opened display on /dev/ttyS0
08/20/12 03:25:09 PM    quokka  LCDd    Key "Escape" is now reserved
exclusively by client [-1]
08/20/12 03:25:09 PM    quokka  LCDd    Key "Enter" is now reserved shared by
client [-1]
08/20/12 03:25:09 PM    quokka  LCDd    Key "Up" is now reserved shared by client [-1]
08/20/12 03:25:09 PM    quokka  LCDd    Key "Down" is now reserved shared by
client [-1]
08/20/12 03:25:09 PM    quokka  LCDd    Key "Left" is now reserved shared by
client [-1]
08/20/12 03:25:09 PM    quokka  LCDd    Key "Right" is now reserved shared by
client [-1]
08/20/12 03:25:09 PM    quokka  LCDd    screenlist_switch: switched to screen
[_server_screen]
08/20/12 03:25:30 PM    quokka  lcdproc Using Configuration File: /etc/lcdproc.conf
08/20/12 03:25:30 PM    quokka  LCDd    Connect from host [127.0.0.1:51238]("http://127.0.0.1:51238") on socket 6
08/20/12 03:25:31 PM    quokka  LCDd    Client [6] is using the menu
08/20/12 03:25:31 PM    quokka  LCDd    Client on socket 6 added added screen "C"
08/20/12 03:25:31 PM    quokka  LCDd    Client on socket 6 added added screen "I"
08/20/12 03:25:31 PM    quokka  LCDd    Client on socket 6 added added screen "M"
08/20/12 03:25:31 PM    quokka  LCDd    Client on socket 6 added added screen "L"
08/20/12 03:25:31 PM    quokka  LCDd    Client on socket 6 added added screen "T"
08/20/12 03:25:31 PM    quokka  LCDd    Client on socket 6 added added screen "P"
08/20/12 03:25:31 PM    quokka  LCDd    Client on socket 6 added added screen "U"
08/20/12 03:25:31 PM    quokka  LCDd    Client on socket 6 added added screen "G"
08/20/12 03:25:31 PM    quokka  LCDd    Client on socket 6 added added screen "N"
08/20/12 03:25:31 PM    quokka  LCDd    screenlist_switch: switched to screen [G]
08/20/12 03:25:36 PM    quokka  LCDd    screenlist_switch: switched to screen [N]
08/20/12 03:25:41 PM    quokka  LCDd    screenlist_switch: switched to screen [C]
08/20/12 03:25:46 PM    quokka  LCDd    screenlist_switch: switched to screen [I]
08/20/12 03:25:51 PM    quokka  LCDd    screenlist_switch: switched to screen [M]
08/20/12 03:25:56 PM    quokka  LCDd    screenlist_switch: switched to screen [L]
```Looks like it is working, right? However, all the LCD is showing is the boot logo.
Any idea how to troubleshoot this?

Related question: I did chmod 666 on /dev/ttyS0, but after a reboot the write permissions for others are gone again. How can I make this change permanent?

---

### Post by Statia on 2012-08-21
Forget it.
After a lot of fiddling, it looks like the serial port is not working, even though it gets reported in dmesg. That was the reason my IR-receiver would not work with lirc as well. I tried connecting a serial mouse, I connected pins 2 and 3 on the port to do a loop-back test, all nothing. Only thing left to conclude is that the port is borked.

---

### Post by Statia on 2012-09-11
Bought a USB version of the same LCD, it works.
I had to recompile the driver for it though. If anyone ever needs help getting this beastie to work, just ask me. However, the support staff at CwLinux is great, they were very helpful in getting it to work.

---

### Post by Yuksel on 2013-03-25
> **Statia said:**
> Bought a USB version of the same LCD, it works.
I had to recompile the driver for it though. If anyone ever needs help getting this beastie to work, just ask me. However, the support staff at CwLinux is great, they were very helpful in getting it to work.

Hi Statia!

I'm an ordinary Ubuntu user and interested in using the CW12832 Graphical USB LCD Module for displaying the stream data (like "now playing" or song name, etc) from vlc player.
How is your experience with the lcd unit? What should I do to get the CW12832 show the "now playing" stuff?

Thanks in advance

---

