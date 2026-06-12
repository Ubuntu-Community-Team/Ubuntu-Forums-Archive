---
title: "Unison; different versions on two machines = Fatal Error"
date: 2012-08-24
forum: General Help
---

### Post by Bucky Ball on 2012-08-24
Hi all,

Attempting to unite a folder on the desktop with a folder on the laptop using Unison. All goes well until the final bit when I get a fatal error that there is a version clash. Ya see, the desktop is running 10.04 and the laptop 12.04, thus Unison 2.2 (I think) and 2.40, respectively. 

From my research I'm thinking there is no way to install 2.4 in 10.04 (attempted it but lacking dependencies I suspect; didn't take a lot of notice but it wouldn't 'make' or 'make install'). So I looked at installing the 3.2 kernel but couldn't figure it out. 

Life doesn't hinge on this but would be nice to know if there was a way around it. ;)

(PS: Am manually dumping stuff from one t'other using Filezilla and a new discovery I like more and more, bareFTP.)

(PPS: I have attempted to use the '-addversionno' option by adding it to the profile file like this:

                       [LEFT]```
path = -addversionno
```[/LEFT]
   Despite the fact I don't know what I'm doing with this and after many failed attempts, all goes well until same version mismatch error.)

---

### Post by dcstar on 2012-08-25
> **Bucky Ball said:**
> Hi all,

Attempting to unite a folder on the desktop with a folder on the laptop using Unison. All goes well until the final bit when I get a fatal error that there is a version clash. Ya see, the desktop is running 10.04 and the laptop 12.04, thus Unison 2.2 (I think) and 2.40, respectively. 

From my research I'm thinking there is no way to install 2.4 in 10.04 .......

Do better research:

[http://thanhsiang.org/faqing/node/163](http://thanhsiang.org/faqing/node/163)

---

### Post by Bucky Ball on 2012-08-25
Please attempt to remain polite. I've actually spent frustrating hours on this and have already been over the ground you're suggesting pretty much (as outlined in post #1) with no success. 2.4 would not install for me on 10.04.

[QUOTE=From Your Link]I downloaded the 2.40 version and installed it at my remote server. The package can be found at the following site:
[https://launchpad.net/~pascal-bach/+archive/unison]("https://launchpad.net/%7Epascal-bach/+archive/unison")[/QUOTE]Done it. As explained, wouldn't install because 10.04 is lacking a dependency I presume (despite the fact it installed for the author of the link). Updating the system from that repository wouldn't work for the same reasons. That is why my next question, in post #1, was how to install the 3.2.** kernel in 10.04. That would have the dependencies for Unison 2.4.

I will go through what I have already done after the footy and take closer note of the errors. No fix and I will follow the steps on your link meticulously and post back.

If no good I'm thinking my only way around this is to install 12.04, which I really don't want to do right now so think I'll stick to the manual dump using bareFTP. It's not really a life-changer for me either way. But I'm certainly curious and it would be more convenient for what I'm doing. ;)

* Yep, I added the repository and updated Unison to 2.4 on 10.04. I haven't tried a 'synthesis' yet, but presuming all will be fine. I was looking for a Unison repo early on but couldn't find, so thanks for digging that up. All in the search terms. Solved.

* A synchronisation throws errors about permissions on one of the machines.

---

### Post by kurt18947 on 2012-08-25
For synchronizing folders on a local machine and external storage - I tried over USB,  not over a network - Luckybackup looks pretty good.  It may work over a network as well - I didn't test that.  It has a synchronize function that did what it promised on a rudimentary test.

---

### Post by Bucky Ball on 2012-08-26
Convenient, worked straight away and I discovered it in my menu by accident: Gigilo. Mounts remote drives like they were local without having to fiddle with fstab. Cool.

Really slow - 40 seconds for 26Mb - is the only prob. It's not Unison but fine for what I want to do. Anyway to speed that up? I might have a dig.

---

### Post by Bucky Ball on 2012-08-26
Convenient, worked straight away and I discovered it in my menu by accident: Gigilo. Mounts remote drives like they were local without having to fiddle with fstab. Cool.

Really slow - 40 seconds for 26Mb - is the only prob. It's not Unison but fine for what I want to do. Anyway to speed that up? I might have a dig.

---

