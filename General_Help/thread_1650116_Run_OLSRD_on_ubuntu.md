---
title: "Run OLSRD on ubuntu"
date: 2010-12-21
forum: General Help
---

### Post by zfima on 2010-12-21
Hello.
I download/install OLSRD and OLSR_SWITCH

Now, i need run multiple instances of OLSRD... But i can not do it.
When i try run two commands:

sudo olsrd -f /etc/olsrd.emu2.conf -hemu 10.0.0.1 -d 1
and 
sudo olsrd -f /etc/olsrd.emu2.conf -hemu 10.0.0.2 -d 1

The error i get from ubuntu os: 

Error, cannot aquire OLSR lock '/var/run/olsrd-ipv4.lock'.
Another OLSR instance might be running

My conf file olsrd.emu2.conf without changes, except of:

DebugLevel    1
IpVersion     4
ClearSCreen   no

but it should not affect something

In site [http://www.olsr.org/docs/README-Olsr-Switch.html]("http://www.olsr.org/docs/README-Olsr-Switch.html") i can read lines: 

"Now for a real world example of connecting olsrd instances. Let's assume we have a modified configuration file, /etc/olsrd.emu.conf that we use for host-emu instances. We'll choose the 10.0.0.0/24 IP address space for our clients."

But, i did not understand meaning of "we have a modified configuration file". How can i do it????

And next line: "Now start the olsrd instances in other terminal(s)." God, how can i do it???!!! I am so stupid or what????

PLEASE, help me run multiple instances!!! It is really important for me!!!

---

### Post by zfima on 2010-12-22
resolved
thanks to all :(

---

### Post by eporto on 2011-03-14
Hey,

Can you please tell me how you did it?

---

### Post by Songshan on 2013-05-02
hi&#65292;zfima! I am using olsr on the ubuntu now. and I want to use olsr_switch,but I do not know how to config and use it , first of all ,how to config olsr.emu.conf ? second,how to load the olsr.emu.conf to the path /etc/olsr.emu.conf ? Can you help me? Thank you!

---

