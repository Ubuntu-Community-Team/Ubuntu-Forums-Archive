---
title: "Ubuntu 9.10 Dialup problem"
date: 2009-12-28
forum: General Help
---

### Post by Superdude_123 on 2009-12-28
Here's what the log from Gnome ppp looks like:

--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT15069550200
--> Waiting for carrier.
ATM1L3DT15069550200
CONNECT 460800 
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
Welcome to Aliant Telecom - Bienvenue ` Telecom Aliant username:
--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Mon Dec 28 18:51:12 2009


And even with stupid mode enabled, it crashes. Oddly enough, in windows it works. What should I do next?

---

### Post by phillw on 2009-12-28
> **Superdude_123 said:**
> Here's what the log from Gnome ppp looks like:
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.


Looks like my good friend permissions.

Not having a dial up modem - I cannot vouch for this .. but ....

```
 ls -l /usr/sbin/pppd 
```on my machine gives me

> -rwsr-xr-- 1 root dip 277352 2009-02-20 17:25 pppd```
 id phillw 
``` gives me
>  uid=1001(phillw) gid=1001(phillw) groups=1001(phillw),4(adm),20(dialout),24(cdrom),46(plugdev),104(lpadmin),114(admin),120(sambashare)


So, I'm not a member of the group dip - and do not have execute privalidges for the file pppd - only read ones. Rather than break the file permissions - try adding yourself to the group dip

```
sudo useradd -g dip [FONT=Verdana]*your_user_name*[/FONT]
```[FONT=Verdana]

If that doesn't work, Soz - I did try !!

Regards,

Phill.
[/FONT]

---

### Post by Superdude_123 on 2009-12-28
Ok, so it seems that I've found a backwards fix.

I've managed to modify the  wvdial.conf file with all the settings, and I've managed to run

 sudo wvdial

to make it work. So now, what could be giving me a exit code = 2 error for pppd?

When I try to use gnome pppd, it fails. What's next?

---

### Post by alexfish on 2009-12-28
> **Superdude_123 said:**
> Here's what the log from Gnome ppp looks like:

--> WvDial: Internet dialer version 1.60
--> Cannot set information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATM1L3DT15069550200
--> Waiting for carrier.
ATM1L3DT15069550200
CONNECT 460800 
--> Carrier detected.  Starting PPP immediately.
--> Unable to run /usr/sbin/pppd.
--> Check permissions, or specify a "PPPD Path" option in wvdial.conf.
Welcome to Aliant Telecom - Bienvenue ` Telecom Aliant username:
--> Timed out while dialing.  Trying again.
--> Maximum Attempts Exceeded..Aborting!!
--> Disconnecting at Mon Dec 28 18:51:12 2009


And even with stupid mode enabled, it crashes. Oddly enough, in windows it works. What should I do next?
hi

can you try these

sudo adduser "YOURUSERNAME" dip

sudo adduser "YOURUSERNAME" dialout

to prove:your groups

code:

id

'''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''
 Be Very Careful here take [COLOR=Navy]Note Of the Original setting And Save To a File[/COLOR]


Code:


gksudo nautilus


navigate to folder[COLOR=Navy] /etc/ppp and right click on pap-secrets[/COLOR] -> Properties -> Permissions tab then select dip from the drop down menu for Group and and then select read and write under Access.[COLOR=Navy] Repeat for chap-secrets[/COLOR]. The annoying warning messages should now disappear.

if it fails :

then you need to check the settings in gnome pppd are correct

details can be found with these commands

code

dmesg | grep "modem"

for the ports

dmesg | grep -e "modem" -e "tty" 


tail -f /var/log/syslog


;

if it fails post details of last 21 lines of the / log file viewer / messages


thanks in advance; do you have any details of the device

alexfish

Check to see if the back end is working from ppp

open  the terminal and test with this code

Code:

sudo apt-get update

---

### Post by Superdude_123 on 2009-12-28
Thanks, that solved it....but for anyone in the future, I had configured the wvdial.conf (I think) file with user name/password/#

---

