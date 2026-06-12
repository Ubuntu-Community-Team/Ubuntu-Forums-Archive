---
title: "upgrade to 11.04 broke bbtether."
date: 2011-05-19
forum: General Help
---

### Post by myurkiw on 2011-05-19
I just upgraded to 11.04 with a fresh install on a Dell Inspiron E1405.  Got everything else working, but can't get my BBTether to work again. 

Message says it usually means the BB is not responding.  But it is also happening with Virgin Mobil Broadband stick.  Both are USB connections.  USB flash drive seems to work.  

BBTether OUTPUT

Will run bbtether with args: ['verizon']
Starting Modem thread
--------------------------------
BBTether 0.3m
Thibaut Colar - 2009
More infos: [http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)
Use '-h' flag for more informations : 'python bbtether.py -h'.
--------------------------------

Looking for USB devices:
    Bus 005 Device 001: ID 1d6b:0001
    Bus 004 Device 001: ID 1d6b:0001
    Bus 003 Device 001: ID 1d6b:0001
    Bus 002 Device 001: ID 1d6b:0001
    Bus 001 Device 006: ID 0fca:8004
    Bus 001 Device 001: ID 1d6b:0002
USB Device lookup finished
Using saved EP data: 0, 130, 2, 131, 3

Using Data Endpoint Pair:0x82/0x2
Using Modem pair: 0x83/0x3

Claiming interface 0
Pin: 0x32978550
Description: RIM BlackBerry Device
System: Linux,2.6.38-8-generic,#42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011,i686

Modem pty: /dev/pts/1
Initializing Modem
No password requested.
session pack sent
Modem Started
Will try to start pppd now, (/usr/sbin/pppd) with config: verizon
Starting Modem thread
********************************************
Modem Ready at /dev/pts/1
 Use ^C to terminate
********************************************
Connect script failed
Error: [Errno 11] Resource temporarily unavailable
******************************************************

Shutting down
Please WAIT for shutdown to complete (up to 30s)
Otherwise you might have to reboot your BB !
******************************************************
Waiting for PPPD shutdown to complete.
PPPD finished
Stopping modem thread
Modem thread Stopped
Disconnected
Releasing interface
bbtether completed.
BBTether Thread completed.


TERMINAL OUTPUT

[sudo] password for mark: 
Reading prefs from /home/mark/.bbtether.conf
Will run bbtether with args: ['verizon']
Starting Modem thread
--------------------------------
BBTether 0.3m
Thibaut Colar - 2009
More infos: [http://wiki.colar.net/bbtether](http://wiki.colar.net/bbtether)
Use '-h' flag for more informations : 'python bbtether.py -h'.
--------------------------------

Looking for USB devices:
    Bus 005 Device 001: ID 1d6b:0001
    Bus 004 Device 001: ID 1d6b:0001
    Bus 003 Device 001: ID 1d6b:0001
    Bus 002 Device 001: ID 1d6b:0001
    Bus 001 Device 006: ID 0fca:8004
    Bus 001 Device 001: ID 1d6b:0002
USB Device lookup finished
Using saved EP data: 0, 130, 2, 131, 3

Using Data Endpoint Pair:0x82/0x2
Using Modem pair: 0x83/0x3

Claiming interface 0
Pin: 0x32978550
Description: RIM BlackBerry Device
System: Linux,2.6.38-8-generic,#42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011,i686

Modem pty: /dev/pts/1
Initializing Modem
No password requested.
session pack sent
Starting Modem thread
Modem Started
Will try to start pppd now, (/usr/sbin/pppd) with config: verizon
********************************************
Modem Ready at /dev/pts/1
 Use ^C to terminate
********************************************
Connect script failed
Failed finding end of line(timeout) for: 
Usually means no reply from the modem
Error: [Errno 11] Resource temporarily unavailable
******************************************************

Shutting down
Please WAIT for shutdown to complete (up to 30s)
Otherwise you might have to reboot your BB !
******************************************************
Waiting for PPPD shutdown to complete.
PPPD finished
Stopping modem thread
Modem thread Stopped
Disconnected
Modem Disconnected
It is now safe to shutdown.
Releasing interface
bbtether completed.
BBTether Thread completed.

---

### Post by ysangkok on 2011-05-19
See this post, it seems he had the same problem as you in his previous post to that thread: [http://ubuntuforums.org/showpost.php?p=7419364&postcount=14](http://ubuntuforums.org/showpost.php?p=7419364&postcount=14)

---

### Post by myurkiw on 2011-05-20
I tried disabling networking and it still did not work.  It doesn't seem to recognize the device is there.  I can't see it in the places folders either.  When I plugged in my BB before, I would get a message on it to use as flash device or something.  Now that doesn't happen.  It is like the USB isn't recognizing something was plugged in.  However, when I plug a thumb drive in, it finds it.

---

### Post by Crimson_Fox on 2011-05-31
It's actually an upstream problem; a change/bug in Debian made it so that relative paths don't work in the scripts anymore.

It's an easy workaround though.  Let's say you untared bbtether in you home folder and you're using the att script.  Just edit /home/<username>/bbtether/conf/att so that the last line uses an absolute path.  For example:

connect "/usr/sbin/chat -f conf/att-chat"

would change to:

connect "/usr/sbin/chat -f /home/<username>/bbtether/conf/att-chat"

---

### Post by myurkiw on 2011-10-20
That did it!!  Thanks.

---

