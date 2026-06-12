---
title: "Unusual pppd/wvdial exit"
date: 2006-05-25
forum: General Help
---

### Post by mindlesscomic on 2006-05-25
I have been running Ubuntu for a day now and love it, having some slight issues with connecting to the net though ( and no I am not inexperianced so don't take that approach :p)

I've properly configured wvdial using the wvdialconf... now I run it and the output is as follows:

zero@Zero:~$ sudo wvdial
--> WvDial: Internet dialer version 1.54.0
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT7670168
--> Waiting for carrier.
ATDT7670168
CONNECT 49333/ARQ/V90/LAPM/V42BIS
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas14.2md1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: [email]lsv620@peoplepc.com[/email]
[email]lsv620@peoplepc.com[/email]
Password:
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 4.248.233.117
    MTU is 1524.
--> Looks like a welcome message.
--> Starting pppd at Thu May 25 01:28:48 2006
--> pid of pppd: 9943
--> [B]Disconnecting at Thu May 25 01:28:48 2006
--> The PPP daemon has died: pppd options error (exit code = 2)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 2)[/B]

Notice the lack of a proper explanation for the exit, the man pages suggest it is an option oriented setting.  My login info is correct, it's connecting fine but for some reason randomly exits.  The config file (wvdial.conf) is the stock one with modifications where necessary (num.,login,pass) nothing more.

Does anyone have any idea what I might do?

(Pon doesn't work as an alternative connection nor does the GUI version, this is the only working method... well semi-working)

I really would appreciate some assistance!

Thank you,
Louis

---

### Post by dmizer on 2006-05-25
found this what may contain your solution: [http://www.linuxforum.com/forums/lofiversion/index.php/t63303.html](http://www.linuxforum.com/forums/lofiversion/index.php/t63303.html)

also "man pppd" shows a more verbose description of error messages.

---

### Post by mindlesscomic on 2006-05-25
Accordingly the exit is caused by attempting to access something only root can aka wvdial is trying to carry out a command only root can.

How do I address this seeing as how the root account in Ubuntu can't be used to login.

---

### Post by towsonu2003 on 2006-05-25
[QUOTE=mindlesscomic]Accordingly the exit is caused by attempting to access something only root can aka wvdial is trying to carry out a command only root can.
[/QUOTE]
try debugging stuff that the website is talking about. 

you use sudo wvdial, so it already has root privileges. it won't care if you can login as root or not as long as you use it with root privileges (sudo). 

also, try putting an option (or both) like ```

Stupid Mode = yes
Carrier Check = no
``` to wvdial.conf

---

### Post by mindlesscomic on 2006-05-25
Thanks for the reply.  Tried the debugging... no results.  Nothing.  I just don't get why it kills the connection.  I've used Wvdial on many other distros including knoppix and no problem.

Below is some more info:

Result of typing PPP after the wvdial fails: 

pppd
pppd: The remote system is required to authenticate itself
pppd: but I couldn't find any suitable secret (password) for it to use to do so.pppd: (None of the available passwords would let it use an IP address.)

Here is my wvdial.conf file:

[Dialer Defaults]
Modem = /dev/ttyS0
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Stupid Mode = Yes
Modem Type = Analog Modem
Phone = 7670168
Username=lsv620@peoplepc.com
Password= (censor)

---

### Post by mindlesscomic on 2006-05-26
Still no ideas? I hate to be a burdon but ... No one else seems to know.

---

### Post by towsonu2003 on 2006-05-27
[QUOTE=mindlesscomic]Still no ideas? I hate to be a burdon but ... No one else seems to know.[/QUOTE]
nope, sorry. I've no clue...

---

