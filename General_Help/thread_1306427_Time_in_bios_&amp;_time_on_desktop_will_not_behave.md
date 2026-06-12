---
title: "Time in bios &amp; time on desktop will not behave bat fine"
date: 2009-10-30
forum: General Help
---

### Post by candive on 2009-10-30
Hi all,

I have an MSI Wind Netbook U-100 running a fresh install of Ubuntu 9.04 updated kernel 2.6.28-16-generic.
 When I set the Bios time the desktop time changes they will not sync.
I just set bios time to 13:21:57 the desktop says 9:21 AM.
When I change the Ubuntu desktop time it changes my bios time.

"What we have here, is a failure to communicate" (Borrowed from Cool hand Luke a movie)

Any Ideas??

Thanks 
Chris.

---

### Post by Monotoko on 2009-10-30
Are you in the right timezone on Ubuntu?

It is most likely the fact that ubuntu is set to the wrong timezone

---

### Post by Giblet5 on 2009-10-30
> **Monotoko said:**
> Are you in the right timezone on Ubuntu?

It is most likely the fact that ubuntu is set to the wrong timezone

Agreed.

You don't have Win7 on that thing do you? It likes to reset BIOS to UTC.

---

### Post by wojox on 2009-10-30
Most BIOS is set to UTC where desktop is region's current time zone.

---

### Post by dearingj on 2009-10-30
edit: I see I was beaten to the punch :)

---

### Post by candive on 2009-10-30
I only have Ubuntu 9.04 on it because winblows.
I originally set my time to Toronto but how do I verify Please.
Thanks 
Chris.

EDIT Just checked preferences my location is blank

---

### Post by candive on 2009-10-30
I just added Toronto to my location.
We will see if that works

Thank you for the help
Chris.

---

### Post by candive on 2009-10-30
Nope, the time in Bios and the time in Ubuntu will not agree.
It causes problems with time stamps in my e mail.
I think I have a compromised system?

Short edited log follows


19:57:31.0794530901 2009 /dev/zero 
+ 5488795  4754   1 root       messagebus     42740 Tue Jul  7 11:19:53.0000000000 2009 /lib/dbus-1.0/dbus-daemon-launch-helper 
+ 5506093   600   1 root       root               0 Thu Oct 29 
+ 4857857  2755   1 root       polkituser     17876 Thu Jan  8 22:19:31.0000000000 2009 /usr/lib/policykit/polkit-explicit-grant-helper 
+ 4857858  2755   1 root       polkituser     17968 Thu Jan  8 22:19:31.0000000000 2009 /usr/lib/policykit/polkit-grant-helper 
+ 4857859  4754   1 root       polkituser      9640 Thu Jan  8 22:19:31.0000000000 2009 /usr/lib/policykit/polkit-grant-helper-pam 
+ 4
+The following programs have got bound sockets: 
troubleshooter@troubleshooter-laptop:~$ sudo chkrootkit 
ROOTDIR is `/' 
                                    no suspect files 
Searching for sniffer's logs, it may take a while...        nothing found 

Searching for suspicious files and dirs, it may take a while... 
/usr/lib/xulrunner-1.9.0.14/.autoreg /usr/lib/firefox-3.0.14/.autoreg /lib/modules/2.6.28-16-generic/volatile/.mounted /lib/init/rw/.ramfs 


Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets 
wlan0: PACKET SNIFFER(/sbin/wpa_supplicant[2971], /sbin/dhclient3[3034]) 
Checking `w55808'...                                        not infected 
Checking `wted'...                                          chkwtmp: nothing deleted 
Checking `scalper'...                                       not infected 
Checking `slapper'...                                       not infected 
Checking `z2'...                                            user troubleshooter deleted or never logged from lastlog! 
troubleshooter@troubleshooter-laptop:~$ 

Thanks 
Chris.
Ps this is a fresh 9.04 from cd loaded and updated yesterday

---

### Post by alphaniner on 2009-10-30
To be clear, the BIOS time and the 'Ubuntu time' are not supposed to agree on the hour.  I think I'm in the same timezone as you, and my BIOS is set to 18:17 and Ubuntu says 14:17.

---

### Post by candive on 2009-10-30
There you go I learned something new.
Thanks
Chris.

---

