---
title: "Intermittent Boot Failure"
date: 2006-01-25
forum: General Help
---

### Post by barryp3uk on 2006-01-25
HI

I'm running Breezy in a dual boot with XP pro. I often get boot failure, particularly if my machine has been switched off for some time. I suspect that it has something to do with my router.

I have a cable modem & router plugged into an ethernet card.

I boot Ubuntu, it fails. I boot windows, everything seems ok with my router.
I boot Ubuntu, it fails. I boot windows & reboot my router
(open 192.168.1.1 & refresh the settings)
I boot Ubuntu. Everything is okay.

Using dynamic ip address.

Error messages on booting:

[B]Calculating module dependencies=Failed
Setting up networking=F
Synchronizing clock with...=F
Initializing random number generator=F[/B]

Then the log screen appears:
For the module dependencies failure it says:

**Fatal:could not open /lib/modules/2.6.12-10-386/modules.dep.temp for writing: read only file system**

At the bottom of the page (maybe relevant) it says:

**/etc/init.d/bootclean.sh: line 42: /tmp.clean: Read-only file system * Starting systen log daemon...   .socket: Address already in usemmn**

I have to c-alt-delete to get away from this page & reboot.

Thanks for any help or advice

Barry.

---

### Post by dcstar on 2006-01-25
[QUOTE=barryp3uk]HI

I'm running Breezy in a dual boot with XP pro. I often get boot failure, particularly if my machine has been switched off for some time. I suspect that it has something to do with my router.

I have a cable modem & router plugged into an ethernet card.

I boot Ubuntu, it fails. I boot windows, everything seems ok with my router.
I boot Ubuntu, it fails. I boot windows & reboot my router
(open 192.168.1.1 & refresh the settings)
I boot Ubuntu. Everything is okay.
......
**/etc/init.d/bootclean.sh: line 42: /tmp.clean: Read-only file system * Starting systen log daemon...   .socket: Address already in usemmn**

I have to c-alt-delete to get away from this page & reboot.

Thanks for any help or advice

Barry.[/QUOTE]
I suspect a hard drive that may be on the point of failure, and only behaves correctly when it has "warmed up" after a minute or two.

Easy way to check is to add a BIOS boot password to your system, fire it up and wait a couple of minutes before allowing it to continue. If it suddenly works after a delay then it isn't the O/S.

---

### Post by barryp3uk on 2006-01-26
Hi David et al,

Thanks for the suggestion.

I tried that but it made no difference. I suspect some corrupt files perhaps.

Any other ideas?

Cheers  

Barry.

---

### Post by johnnymo87 on 2006-01-26
I have *exactly* the same problem. I talked about it in this thread: [http://www.ubuntuforums.org/showthread.php?t=117256](http://www.ubuntuforums.org/showthread.php?t=117256). Basically, my hard drive is old and dying, and your's may be as well.

---

### Post by barryp3uk on 2006-01-26
Hi Johnny

Thanks for your reply.

I read your thread but my HDD was bought last June, is new, & today I downloaded the maker's (Maxtor) disc checking utility. It ran all afternoon & told me that physically my disc was fine.

The thing which makes a difference, as crazy as it sounds, is rebooting my router when in Windows.

Cheers!

Barry.

---

### Post by cws on 2006-01-28
I got an exactly same problem when following the steps in this howto [http://ubuntuforums.org/showthread.php?t=107856](http://ubuntuforums.org/showthread.php?t=107856) 

I believe it relates to /etc/fstab line "**errors=remount-ro**"

My whole system is now read-only and I can't do anything even in the recovery mode :???: 

I would appreciate if someone could tell us how we can make our systems back to rw so it would be possible to undo those changes that led to this?

EDIT: ```
mount -o remount,rw /
``` fixed it for me.

---

### Post by rockstar on 2006-01-29
I am dual booting Windows Xp Pro and Ubutu with a Dell XPS laptop.  Occasionally when I choose to boot windows, I select it from the boot menu and windows shows the loading screen, but then changes to a black screen.  If I manually turn it off it will boot in safe mode.  Sometimes If I boot it in safe mode, restart, and then it will boot normally.  Ubutnu has never had a problem booting.  The OSes are on the same hard drive but on sepporate partitions.

Is there any way that Ubutu is causing trouble with windows?

---

### Post by barryp3uk on 2006-01-31
Hi folks!

Barry here. I decided maybe my manual partitioning had caused some kind of problem so as a control experiment I bought a new maxtor slave drive  (didn't break the bank) & did a clean automatic (I mean erase drive & install Ubuntu) install onto it. The partitions turned out pretty much the same as my manual ones.

Anyway, guess what? I have exactly the same problem!

It's not just a case of "calculating module dependencies" failing because the HDD is compromised. I'm still convinced that the router has something to do with it.

Been reading up on router issues here in this forum & elsewhere. One comment someone made somewhere when discussing a problem similar to my own was interesting. They said:

"It's possible that the router is losing the original DHCP allocation somewhere after a period of time." I pretty well know what this means I think, but can someone explain 

how that could happen, 
what one could do about it 
& wheter it would set into motion a boot failure.

BTW when I can boot I often can't get online but I can't even ping the router at 192.168.1.1

When things are Ok I can do this no problem.

Sorry if this isn't specific to Ubuntu. In Win XP pro I sometimes need to reboot the router, about once a week. Could be the same thing.

Cheers!

Barry.

---

### Post by barryp3uk on 2006-01-31
BTW

Dear CWS

with the respect to the error line in /etc/fstab

I just edited it out & replaced it with the variables I wanted.

sudo gedit /etc/fstab

Cheers!

Barry.

---

### Post by barryp3uk on 2006-02-01
Hi everyone!

I cracked it, as far as I can tell!

[QUOTE=barryp3uk]It's not just a case of "calculating module dependencies" failing because the HDD is compromised. I'm still convinced that the router has something to do with it.[/QUOTE]

Defintely, it was the router. My advice to any newbies like me re: module dependencies is that problems may be hardware related  *but not necessarily the disk * as is often suggested in this forum.

I'm pretty sure that I was right about it being my router.

I found someone who remarked:

> It's possible that the router is losing the original DHCP allocation somewhere after a period of time

& asked

> how that could happen, 

Because I never switch off my cable modem (NTL in the UK) & because power outages cause  connection problems I was leaving the router on all the time too. Since I started switching it off when I finished work the problem has completely vanished. I think that it was losing its settings becuase it was constantly "hot".

> what one could do about it 

Obvious. Switch it off. I have a neat surge protector which automatically switches off peripherals plugged into it when the computer powers down.

> & whether it would set into motion a boot failure.

Yes, it did. No boot failures since the change.

Thanks to everyone who has read this thread or tried to be helpful.

See you again with my next misadventure!  ;)

Cheers!
 
Barry.

---

### Post by barryp3uk on 2006-02-23
Hi Everyone!

I want to revive this thread, if I may; I spoke too soon. All settled down but now exactly the same problem has appeared again:

Module dependencies  & networking failure.

NB  My hard drive is OK. I bought A new slave drive & installed Breezy onto it no prob.

The problem seems to have got worse since the last update. (Not sure how to identify an update once it's come down & been installed.)

Interesting point: if after boot fails I press C-A-D the second time it will fail but the third time it all seems to work.

QU: would the router cause module dependencies failure as I suspected earlier? 

Ifconfig  says:

> eth0      Link encap:Ethernet  HWaddr 00:40:F4:5D:72:30
          inet addr:86.20.33.216  Bcast:255.255.255.255  Mask:255.255.252.0
          inet6 addr: fe80::240:f4ff:fe5d:7230/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:408 errors:0 dropped:0 overruns:0 frame:0
          TX packets:283 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:302974 (295.8 KiB)  TX bytes:29432 (28.7 KiB)
          Interrupt:11 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6603 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6603 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1148742 (1.0 MiB)  TX bytes:1148742 (1.0 MiB)

I'm on eth0 of course.

[B]If I manage to boot without the network then I can't even ping 192.168.1.1
[/B]
Grateful for any help. It's a pain & although I am happy to climb the learning curve & tweak away at things I'm getting discouraged. 

Thanks!

Barry.

---

### Post by barryp3uk on 2006-03-10
Hi

It case anyone may be interested I replaced the IDE cable & the problem seems to have sorted itself out. As it has always been an intermittent problem maybe it will recur but so far seems OK.

So not disk failure! 

Cheers!

Barry.:mrgreen:

---

