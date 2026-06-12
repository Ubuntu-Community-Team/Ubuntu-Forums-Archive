---
title: "scanModem"
date: 2006-04-26
forum: General Help
---

### Post by cssutto on 2006-04-26
Running scanModem and following its instructions brings me to:

thinkpad:/tmp$ wvdialconf wvtest
Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47  S48
Port Scan<*1>: S49  S50  S51  S52  S53


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at [http://open.nit.ca/wvdial/](http://open.nit.ca/wvdial/)

If you still have problems, send mail to [email]wvdial-list@lists.nit.ca[/email].


This is when trying to set up the Acer '97 modem that is internal to my ThinkPad.

However, I have an old PCIMA (???? I never could remember those initials) from my old laptop and it works.  Also, this same test will find it and give it a good bill of health.

However, nothing I have tried gets close to the internal Acer '97.

What do I try next?

CSSJR

---

### Post by towsonu2003 on 2006-04-26
Can you attach your ModemData.txt and also post the steps you followed? In the meantime, check out the wiki page (second link in my signature) to see if it has instructions for your particular modem. 

From what I see, modem is not configured at all (linux doesn't see it). Check it out at System>Administration>Networking (to see if it shows a modem interface).

---

### Post by cssutto on 2006-04-26
[QUOTE=towsonu2003]Can you attach your ModemData.txt and also post the steps you followed? In the meantime, check out the wiki page (second link in my signature) to see if it has instructions for your particular modem. 

From what I see, modem is not configured at all (linux doesn't see it). Check it out at System>Administration>Networking (to see if it shows a modem interface).[/QUOTE]


I just fixed it.

However, I can run it only from the command line as sudo wvdial.

This will not be good when I am traveling.

I tried to run  sudo gedit $HOME/.wvdial.conf
, but all I could get was a blank page.

CSSJR

---

### Post by cssutto on 2006-04-26
[QUOTE=towsonu2003]Can you attach your ModemData.txt and also post the steps you followed? In the meantime, check out the wiki page (second link in my signature) to see if it has instructions for your particular modem. 

From what I see, modem is not configured at all (linux doesn't see it). Check it out at System>Administration>Networking (to see if it shows a modem interface).[/QUOTE]

, 

By the way, all of the reading I did for the past several days was of no use until I was referred to [https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29)

I highly recommend that anyone with a modem problem do the scanModem thing and then go to [https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28modem%29) for the wind up.

CSSJR

---

### Post by towsonu2003 on 2006-04-27
[QUOTE=cssutto]I just fixed it.
[/quote]excellent \\:D/ 
[QUOTE=cssutto]
However, I can run it only from the command line as sudo wvdial.
[/quote]that's how it supposed to work
[QUOTE=cssutto]
This will not be good when I am traveling.

I tried to run  sudo gedit $HOME/.wvdial.conf
, but all I could get was a blank page.

CSSJR[/QUOTE]
I'm not sure if I understand the problem. But I am guessing, even if I did understand it, I wouldn't be able to help with it, bc I think you want either a number of wvdial.conf files to use, or many accounts in one wvdial.conf file. I don't use it like that, so I don't have experience with it. Have a look at ```
man wvdial
man wvdial.conf
```
----either one of the above I believe-----
bc i remember seeing a section about multiple phone numbers / accounts in one wvdial.conf in there. There should also be an option (saw it, don't remember -using windows now from work) to tell wvdial to use a particular configuration file instead of the default /etc/wvdial.conf... sorry not much helping here... 

sudo gedit $HOME/.wvdial.conf won't work bc the default configuration file is in /etc/wvdial.conf (have a backup of it before starting to edit). 
PS. so the command would be sudo gedit /etc/wvdial.conf

be careful with the permissions of wvdial.conf: it has your ISP password in plain text... it should be readable&writable by root only (nothing else).

---

