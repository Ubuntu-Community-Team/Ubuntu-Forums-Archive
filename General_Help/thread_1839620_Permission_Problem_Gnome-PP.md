---
title: "Permission Problem Gnome-PP"
date: 2011-09-06
forum: General Help
---

### Post by frank cox on 2011-09-06
I am trying to get a connection using a cheap USB Winmodem from Ebay . 

[http://www.ebay.com/itm/External-56K-USB-2-0-V-92-Dial-Up-Voice-Fax-Data-Modem-/120749146250?pt=PCC_Modems&hash=item1c1d35c08a](http://www.ebay.com/itm/External-56K-USB-2-0-V-92-Dial-Up-Voice-Fax-Data-Modem-/120749146250?pt=PCC_Modems&hash=item1c1d35c08a)

These have been found automatically by every form of Ubuntu I have tried them on and Puppy Linux as well.
On Puppy is is a no brainer, on Ubuntu I have only managed to get them to work by typing :
sudo Gnome-PPP .

I have copied every file I could think of and a list that might help diagnose the trouble plus some  from. another post here  There are 2 paste bin files and the links are below. They are listed as Gnome-PPP and Gnome-PPP #2

 [http://pastebin.com/e0yG8n7P](http://pastebin.com/e0yG8n7P)    [http://pastebin.com/24wh89Dd](http://pastebin.com/24wh89Dd)

It certainly seems to be a permission problem as it works fine logged on as sudo but that is not obviously the best way to go.  Any help would be appreciated!

---

### Post by _duncan_ on 2011-09-07
```
sudo adduser [COLOR="Blue"]yourUserID[/COLOR] dip
```
The command will add your user ID to the 'dip' group, which already has the necessary permissions by default.

Remember to log out and log back in after executing the command for the changes to take effect.

---

### Post by frank cox on 2011-09-07
> **_duncan_ said:**
> ```
sudo adduser [COLOR=Blue]yourUserID[/COLOR] dip
```The command will add your user ID to the 'dip' group, which already has the necessary permissions by default.

Remember to log out and log back in after executing the command for the changes to take effect.


I am already a member of dip. Also checked to make sure I was a member of dialout. 

This is the info from the logfile.
--> WvDial: Internet dialer version 1.61
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT2994138
--> Waiting for carrier.
ATM1L3DT2994138
CONNECT 115200
--> Carrier detected.  Waiting for prompt.
Level 3 Comm nas9.nvl1 UQKT2
Username:/login:/Login:
--> Looks like a login prompt.
--> Sending: [EMAIL="fpcharnock@natblast.com"]Username@somewhere.com[/EMAIL]
[EMAIL="Username@natblast.com"][/EMAIL]
Password: 
--> Looks like a password prompt.
--> Sending: (password)
    Entering PPP Session.
    IP address is 4.152.180.209
    MTU is 1500.
--> Looks like a welcome message.
--> Starting pppd at Wed Sep  7 10:28:01 2011
--> Warning: Could not modify /etc/ppp/pap-secrets: Permission denied
--> --> PAP (Password Authentication Protocol) may be flaky.
--> Warning: Could not modify /etc/ppp/chap-secrets: Permission denied
--> --> CHAP (Challenge Handshake) may be flaky.
--> Pid of pppd: 3348
--> Disconnecting at Wed Sep  7 10:28:01 2011
--> The PPP daemon has died: No root priv error (exit code = 3)
--> man pppd explains pppd error codes in more detail.
--> I guess that's it for now, exiting
--> The PPP daemon has died. (exit code = 3)
Thanks

---

### Post by frank cox on 2011-09-07
Someone suggested I try chmod +s /usr/sbin/pppd .  Then it would not find the modem so I cut the speed back to 46000 and it worked!


Here is the solution to chap pap secrets permission errors

Chap/pap secrets permission  error fix
[http://linmodems.technion.ac.il/archive-sixth/msg04656.html](http://linmodems.technion.ac.il/archive-sixth/msg04656.html)

---

