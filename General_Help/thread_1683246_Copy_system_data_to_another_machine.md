---
title: "Copy system data to another machine"
date: 2011-02-07
forum: General Help
---

### Post by e24ohm on 2011-02-07
Folks:
I am looking for a way to see if it is possible to copy the system state of a system to another system.

Is it possible to simply move the folder structure over to another machine, and have it work? Do I need any special partitions for /var, /home, etc…?

My machine is dying slowly, and I really want the quickest way to migrate the system over to the new system.

Thanks.

---

### Post by ahsan101 on 2011-02-07
You can use live cd feature, build the live cd of your system and install it on other machine and then from USB paste the data......(this helped my friend once he was using ubuntu 8)

---

### Post by e24ohm on 2011-02-07
> **ahsan101 said:**
> You can use live cd feature, build the live cd of your system and install it on other machine and then from USB paste the data......(this helped my friend once he was using ubuntu 8)

I have never used the LIVE cd feature. Does this utility copy the system state? I have a few Apache modules installed as well - will it copy these as well?

---

### Post by ahsan101 on 2011-02-07
Yeah, you can use ghost as well, it will make the image and deploy it to the other system you want + no worries, it will copy the system state as well, you can google for ReMaster Sys or something like this, i forgot i used before for deploying ubuntu on 24 computers in an internet cafe. the best method i will prefer is to use the Ghost via USB and make the image and first test to deploy it on other machine, and i am pretty sure it will work out!! :)

Checkout this 

[www.geekconnection.org/remastersys/](www.geekconnection.org/remastersys/) 


@Edit : ReMaster Sys link, you will find the guide there.

---

### Post by e24ohm on 2011-02-07
> **ahsan101 said:**
> Yeah, you can use ghost as well, it will make the image and deploy it to the other system you want + no worries, it will copy the system state as well, you can google for ReMaster Sys or something like this, i forgot i used before for deploying ubuntu on 24 computers in an internet cafe. the best method i will prefer is to use the Ghost via USB and make the image and first test to deploy it on other machine, and i am pretty sure it will work out!! :)

Checkout this 

[www.geekconnection.org/remastersys/](www.geekconnection.org/remastersys/) 


@Edit : ReMaster Sys link, you will find the guide there.

Hey thanks mate...this looks like it will work...cheers!!!

---

### Post by ahsan101 on 2011-02-07
> Hey thanks mate...this looks like it will work...cheers!!!

You are most welcome :)

---

### Post by rubylaser on 2011-02-07
Another option would be to boot from the ubuntu rescue remix live cd, and then use gddrescue.
```
ddrescue -v /dev/sda /dev/sdb
```

That will make a perfect copy from one drive to the other.

---

### Post by e24ohm on 2011-02-07
> **rubylaser said:**
> Another option would be to boot from the ubuntu rescue remix live cd, and then use gddrescue.
```
ddrescue -v /dev/sda /dev/sdb
```

That will make a perfect copy from one drive to the other.

This might be what I am looking for, since I was looking at the DD command; however, I am not familiar with the ddrescue command, so thanks for mentioning it.

---

