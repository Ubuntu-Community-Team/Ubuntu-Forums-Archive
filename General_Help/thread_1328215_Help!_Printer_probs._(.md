---
title: "Help! Printer probs. :("
date: 2009-11-16
forum: General Help
---

### Post by katkinn on 2009-11-16
I have a Canon MP190 and I am having problems printing. Everything is hooked up correctly, but when I try to print it says that my printer may not be connected.

I have gone into Printing and there is a green tick next to my printer, but I'm not sure what that means.

Could someone let me know how I reconnect it please?

Thanks,

Kat

---

### Post by jsgarvin on 2009-11-16
Same issue here I think.  I printed to this printer (Lexmark C534) just fine last week. This morning I can't print to it and Printer Properties report the status as "Idle - /usr/lib/cups/backend/dnssd failed"

coworkers on Macs can print to the same printer just fine.

---

### Post by jsgarvin on 2009-11-20
bump

---

### Post by khelben1979 on 2009-11-20
Check with [Synaptic]("http://en.wikipedia.org/wiki/Synaptic_package_manager") to see if [CUPS]("http://en.wikipedia.org/wiki/CUPS") is installed.

---

### Post by leoh on 2010-01-27
> **jsgarvin said:**
> Same issue here I think.  I printed to this printer (Lexmark C534) just fine last week. This morning I can't print to it and Printer Properties report the status as "Idle - /usr/lib/cups/backend/dnssd failed"
Same problem here with another Lexmark (E120).
I am using Ubuntu 9.10 x64.
This is a recently installed system, and the printer worked just fine when I first installed it.
I just tried to print a test page, and the printer queue says "processing" since I sent the job, about 15 mins ago.
What is the "/usr/lib/cups/backend/dnssd failed" error code???

Also, as I was writing this, my session logged out (never happened before). No idea if related to this.

---

### Post by Tux+ on 2010-01-27
> **khelben1979 said:**
> Check with [Synaptic]("http://en.wikipedia.org/wiki/Synaptic_package_manager") to see if [CUPS]("http://en.wikipedia.org/wiki/CUPS") is installed.

Also you can try the printer driver database:
[http://www.openprinting.org/driver_list.cgi](http://www.openprinting.org/driver_list.cgi)

---

### Post by dpetroni on 2010-02-08
The "/usr/lib/cups/backend/dnssd failed" error is usually the consequence of avahi-daemon not running on the system. Check if it is installed at all and if it is try restarting it. I can't tell you how to do it since I am not familiar with upstart - the new Ubuntu startup mechanism. In Debian it is simple: /etc/init.d/avahi-daemon restart.

Perhaps it would still work in Ubuntu.

---

### Post by gandalf2000 on 2010-02-10
I am having the same trouble and I don't know when things went wrong.  Avahi deamon is running.  On the system monitor it says:- avahi-daemon: chroot helper  sleeping
and immediately beneath it says:- avahi-daemon: running[gandalf.local]  sleeping.

Any ideas?

---

### Post by gandalf2000 on 2010-02-10
Managed to get it working using this thread.
[http://ubuntuforums.org/showthread.php?t=1373928](http://ubuntuforums.org/showthread.php?t=1373928)

---

### Post by SZVSZ on 2010-03-09
> **dpetroni said:**
> The "/usr/lib/cups/backend/dnssd failed" error is usually the consequence of avahi-daemon not running on the system. Check if it is installed at all and if it is try restarting it. I can't tell you how to do it since I am not familiar with upstart - the new Ubuntu startup mechanism. In Debian it is simple: /etc/init.d/avahi-daemon restart.

Perhaps it would still work in Ubuntu.

thanks for this tip, this did work for me:

sudo service avahi-daemon restart

---

### Post by dlublink on 2012-05-29
I had a similar problem, it started after I changed the hostname of my laptop. Make sure that the value in /etc/hostname is also in /etc/hosts pointing to 127.0.0.1

---

### Post by oldos2er on 2012-05-29
Old thread closed. Please don't bump old threads.

---

