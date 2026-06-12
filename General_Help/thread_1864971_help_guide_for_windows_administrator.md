---
title: "help guide for windows administrator"
date: 2011-10-19
forum: General Help
---

### Post by petatras on 2011-10-19
Hi, I'am a microsoft system administrator  that would like migrate to ubuntu system administrator.

I know windows server repair problems, both startup problems, including problems with files such as problems with services, domains, etc ...
 The question is, is there some sort of guide or equivalence to solve problems, for example if something goes wrong in Windows will automatically look for the solution in the event viewer, what it would be in Ubuntu?

Thanks

---

### Post by ubudog on 2011-10-19
Normally if I don't know how to fix something in Linux, I just Google it.  There are many friendly guides out there for many things.

---

### Post by seawolf167 on 2011-10-19
You can look in the logs, located in /var/logs

There is also a server guide located here:
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by petatras on 2011-10-19
hi, thanks for your help, and yes me too , when i have a problem i search in google , but I meant more like a preventive maintenance, this is what is known in Spain as "prevention rather than cure", and if there is some guidance to make linux server maintenance. 

And thnk for var/logs,

---

### Post by ubudog on 2011-10-19
> **petatras said:**
> hi, thanks for your help, and yes me too , when i have a problem i search in google , but I meant more like a preventive maintenance, this is what is known in Spain as "prevention rather than cure", and if there is some guidance to make linux server maintenance. 

And thnk for var/logs,
+1 for the server guide.

Some preventative/security stuff you could do would be:
[LIST=1]
[*]Make sure to lock down your webserver
[*]Install fail2ban for ssh ddos prevention
[*]The firewall comes locked down, but you may want to tweak it (be careful)
[*]Be sure not to run unknown programs as root (eg. sudo unknownprogram)
[/LIST]

Hope that helps, good luck!

---

### Post by collisionystm on 2011-10-19
> **petatras said:**
> Hi, I'am a microsoft system administrator  that would like migrate to ubuntu system administrator.

I know windows server repair problems, both startup problems, including problems with files such as problems with services, domains, etc ...
 The question is, is there some sort of guide or equivalence to solve problems, for example if something goes wrong in Windows will automatically look for the solution in the event viewer, what it would be in Ubuntu?

Thanks

Are you looking to replace your windows server with a Linux box or simply just trying to educate yourself?

---

### Post by petatras on 2011-10-27
Thanks for your answers ubudog, and yes i simply just trying to educate myself,  I'm looking for some knowhow in ubuntu-debian.

---

### Post by linuxwin2 on 2011-10-27
Look this guide
[http://tldp.org/LDP/sag/sag.pdf](http://tldp.org/LDP/sag/sag.pdf)

---

### Post by coldraven on 2011-10-27
Loads of tutorials here: [http://www.howtoforge.com/howtos/linux/ubuntu](http://www.howtoforge.com/howtos/linux/ubuntu)

---

