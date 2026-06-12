---
title: "Ubuntu machine slowing down my network"
date: 2011-07-14
forum: General Help
---

### Post by Colo2 on 2011-07-14
Hello

Recently, we've been having some pretty extreme slow internet. Like, having 3000 ping on gameservers, and having to wait 20 seconds for gmail to appear, so we decided to turn off each PC in the house in turn to diagnose which PC was the offending one.

The PC turned out to be my ubuntu homeserver. When turned off, the internet runs fluidly, when turned on, no one can use the internet.

Nothing is visibly happening on the ubuntu machine. After a boot, SAMBA, Apache2 and MySQL start up, but thats about it I think.

Please help me find the offending and put a stop to it

thanks

Tom

---

### Post by SavageWolf on 2011-07-14
Why do you have Apache and MySQL on it?

---

### Post by Colo2 on 2011-07-14
> **SavageWolf said:**
> Why do you have Apache and MySQL on it?

I use it as a web server aswell. But to my knowledge, Its only used internally as a webserver.

---

### Post by Colo2 on 2011-07-14
After turning the ubuntu machine off, my ping dropped from 3k, to 64 on a gameserver. I dont understand, I need this machine, but I cant have it sucking up my connection like this.

---

### Post by SavageWolf on 2011-07-14
Have tried seeing what happens if you kill Apache?

And what do you use this webserver for?

---

### Post by Grenage on 2011-07-14
> **Colo2 said:**
> Hello

Recently, we've been having some pretty extreme slow internet. Like, having 3000 ping on gameservers, and having to wait 20 seconds for gmail to appear, so we decided to turn off each PC in the house in turn to diagnose which PC was the offending one.

The PC turned out to be my ubuntu homeserver. When turned off, the internet runs fluidly, when turned on, no one can use the internet.

Nothing is visibly happening on the ubuntu machine. After a boot, SAMBA, Apache2 and MySQL start up, but thats about it I think.

Please help me find the offending and put a stop to it

thanks

Tom

Something is obviously very wrong with that install, what exactly was it configured to do?  Check the output of:

```
netstat -t -u
```

I'm assuming that the machine is either misconfigured, running torrents, or compromised in some way - but it could be anything, even a bad cable.  You'll need to rule out one thing at a time, both software and hardware.

---

### Post by Colo2 on 2011-07-14
Hello

The output is as follows:

```
dump@STORAGE-DUMP:~$ netstat -t -u
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0  43200 STORAGE-DUMP:www        ip-216-115-150-11:64163 ESTABLISHED
tcp        0      0 STORAGE-DUMP:5900       192.168.1.149:51883     ESTABLISHED
tcp        0  39440 STORAGE-DUMP:www        59.103.197.64:3702      ESTABLISHED
tcp        0  25840 STORAGE-DUMP:www        59.103.197.64:3698      ESTABLISHED
tcp        0  63360 STORAGE-DUMP:www        184-98-114-219.ph:60642 ESTABLISHED
tcp        0  64800 STORAGE-DUMP:www        207-118-242-32.dy:50008 ESTABLISHED
tcp        0  36720 STORAGE-DUMP:www        59.103.197.64:3703      ESTABLISHED
tcp        0  43520 STORAGE-DUMP:www        59.103.197.64:3701      ESTABLISHED
tcp        0      0 localhost.localdo:58224 localhost.localdo:46560 TIME_WAIT  
tcp        0  47600 STORAGE-DUMP:www        59.103.197.64:3699      ESTABLISHED
dump@STORAGE-DUMP:~$ 

```

---

### Post by Colo2 on 2011-07-14
Can anyone help?

---

### Post by Grenage on 2011-07-14
Sorry for the delayed reply, it's been a busy day.  I don't have any instances of Apache at home, only work - so I can compare it to one of ours then.

As previously suggested, does stopping MySQL or Apache stop the network throttling from occuring?

---

### Post by Colo2 on 2011-07-14
Hey, no problem, thanks for replying. 

Uhm, I think I was wrong, MySQL isn't running on that PC, was never needed, so it's just apache2.

Apache2 was stopped with service apache2 stop, but made absolutely no difference. 

:S The only thing I use this PC for is streaming music and videos within my local network, I've disabled DMZ, and there are no ports forwarded.

Tom

---

### Post by linuxuser12345 on 2011-07-14
Try using Ubuntu 10.04.2. It is by far the most stable Ubuntu, and will most likely give you the least (if any) problems. Go 64-bit if you can

---

### Post by Colo2 on 2011-07-14
:popcorn:

Unfortunately, formatting isn't an option, being that it has hundreds of GBs of data on it that I cant transfer over to another disk, cant partition because then I;d have to move data from partition to partition.

Is there a way to install 10.04 without changing my settings... only changing the system and system files.

Also, any possibility of this being a HW problem?

---

### Post by Grenage on 2011-07-15
> **Colo2 said:**
> :popcorn:

Unfortunately, formatting isn't an option, being that it has hundreds of GBs of data on it that I cant transfer over to another disk, cant partition because then I;d have to move data from partition to partition.

Is there a way to install 10.04 without changing my settings... only changing the system and system files.

Also, any possibility of this being a HW problem?

I've not used it before, but iptraf is supposed to be both easy and excellent at listing traffic volume and destination.

As for hardware, it's absolutely possible that a hardware fault could cause this; the primary candidate would be the network card, with the cable having a low outside chance.  Check the traffic first, since that requires the least effort. ;)

---

### Post by Colo2 on 2011-07-15
Hey

thanks so much for your help.

The problem was a faulty network card, just put a different on in and works fine now! 

It seemed that, also something was targeting it's internal IP, I changed it in Ubuntu and now the ping remains the same when the STORAGE DUMP is on

Thanks again :)

Off topic: @ Grenage, I was born in Portsmouth! :-& busy place!!!

---

### Post by Grenage on 2011-07-15
> **Colo2 said:**
> Hey

thanks so much for your help.

The problem was a faulty network card, just put a different on in and works fine now! 

It seemed that, also something was targeting it's internal IP, I changed it in Ubuntu and now the ping remains the same when the STORAGE DUMP is on

Thanks again :)

Off topic: @ Grenage, I was born in Portsmouth! :-& busy place!!!

It's always delightful when things are that quick to fix!

A very busy place indeed; hopefully I'll not be here too much longer. ;)

---

