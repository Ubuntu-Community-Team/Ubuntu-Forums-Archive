---
title: "Efax, Linuxant modeminstalled: can't open serial port"
date: 2009-11-16
forum: General Help
---

### Post by Dutch on 2009-11-16
Hi,

Trying to make Efax work. Downloaded the Linuxant driver trough cnxtinstall.run

Efax
Serial Device:  ttySHSF0

But with sending a fax, the Efax programm give's this
```

efax-0.9a: 23:13:26 Error: can't open serial port /dev/ttySHSF0: Permission denied
```

```

paul@ibm:/$ sudo wvdialconf
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   
ttySHSF0<*1>: ATQ0 V1 E1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 Z -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySHSF0<*1>: Modem Identifier: ATI -- 56000
ttySHSF0<*1>: Speed 4800: AT -- OK
ttySHSF0<*1>: Speed 9600: AT -- OK
ttySHSF0<*1>: Speed 19200: AT -- OK
ttySHSF0<*1>: Speed 38400: AT -- OK
ttySHSF0<*1>: Speed 57600: AT -- OK
ttySHSF0<*1>: Speed 115200: AT -- OK
ttySHSF0<*1>: Speed 230400: AT -- OK
ttySHSF0<*1>: Speed 460800: AT -- OK
ttySHSF0<*1>: Max speed is 460800; that should be safe.
ttySHSF0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
Modem Port Scan<*1>: SHSF2 SHSF3 SHSF4 SHSF5 SHSF6 
Modem Port Scan<*1>: SHSF7 

Found a modem on /dev/ttySHSF0.
Modem configuration written to /etc/wvdial.conf.
ttySHSF0<Info>: Speed 460800; init "ATQ0 V1 E1 
```

If you need more info, let me know.



Ubuntu 8.04
PIV 3 Ghz.

---

### Post by Giblet5 on 2009-11-16
Open a terminal window and enter

```
sudo chmod 666 /dev/ttySHSF0
```

Now try.

(Your user account wasn't allowed to open the device for read/write. Now it is.)

---

### Post by Dutch on 2009-11-16
Thank you Giblet !

Where can I learn about that chmod things ? (Uhhhmm chmod *666* :-)

One thing, how can I make the modem byp ?
So I now it&#347; busy sending ore receiving a Fax ?

---

### Post by Giblet5 on 2009-11-16
Open a terminal window and enter ```
man chmod
```

When you use 'ls -l' to list files and directories, it lists a string of permissions on the left, like ```
drwxr-xr-x owner group blahblahblah
```

The permissions, or "mode". of the file determine who can/can't access it.

The first position is the special flag (d = directory, b = block device, c = character device, etc).

The next nine characters determine the Read, Write, and eXecute permissions for Owner, Group, and Others.

Take each 'octet' (three values of read/write/execute) and the positions can be interpteted as octal values: 0 = all bits off (--- in ls -l) through 7 = all bits on (rwx in ls -l).

666 on a tty will be crw-rw-rw- (owner, group, and others can read or write the device)

Easy as mud, huh?


I don't know how to make a modem byp. What is byp?

---

### Post by Dutch on 2009-11-16
Yah you saw what my problem was :-)

Thanks for the explanation.

Sorry, I ment Beep. The sounds the modem makes while sending the fax.
With my former installation I heard a sound while sending a fax.

---

### Post by Giblet5 on 2009-11-17
That's a modem command, "AT M1" (turn the speaker on until connect), and "AT Ln" (Set speaker volume to 'n').

A command that I like to add is "AT S11=55" which sets the inter-tone delay to 55 milliseconds. It will dial in half the time, it is well within the dialing specs of even the oldest PBX systems (AT&T Definity G3, now owned by Avaya), and it sounds much cooler. ;)


Here's a [handy modem command reference]("http://support.microsoft.com/kb/164660"). This is often referred-to as the Hayes command set, even though Hayes has less to do with it than US Robotics and 3Com.

---

