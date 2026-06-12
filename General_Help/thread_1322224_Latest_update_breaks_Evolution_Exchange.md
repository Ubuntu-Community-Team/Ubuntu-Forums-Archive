---
title: "Latest update breaks Evolution Exchange"
date: 2009-11-10
forum: General Help
---

### Post by muecker on 2009-11-10
I just installed a bunch of Karmic updates and rebooted my machine.  Included among those updates were several updates to Evolution.  Now I cannot receive mail via the Evolution Exchange connector.  It was working prior to the updates now the backend crashes with the following messages:

From messages:
```

Nov 10 16:34:27 muecker-dt kernel: [  183.735652] __ratelimit: 6 callbacks suppressed
Nov 10 16:34:27 muecker-dt kernel: [  183.735657] evolution-excha[3441]: segfault at 10 ip 00007fd599161479 sp 00007fd5896e33e0 error 4 in libsoup-2.4.so.1.3.0[7fd599137000+4b000]
Nov 10 16:35:42 muecker-dt kernel: [  258.687309] evolution-excha[3691]: segfault at a ip 00007f92f3b103c6 sp 00007f92dfffe3d0 error 4 in libc-2.10.1.so[7f92f3a98000+166000]
Nov 10 16:36:03 muecker-dt kernel: [  279.438065] evolution-excha[3825]: segfault at 7f1d0000000a ip 00007f1d2bf733c6 sp 00007f1d1c9d3680 error 4 in libc-2.10.1.so[7f1d2befb000+166000]
Nov 10 16:37:07 muecker-dt kernel: [  343.440449] evolution-excha[3905]: segfault at 10 ip 00007f9fecf4b479 sp 00007f9fddcce3e0 error 4 in libsoup-2.4.so.1.3.0[7f9fecf21000+4b000]
Nov 10 16:40:25 muecker-dt kernel: [  542.337921] evolution-excha[4180]: segfault at 7f750000000a ip 00007f7577d15eda sp 00007f75637fba90 error 4 in libc-2.10.1.so[7f7577ca0000+166000]
Nov 10 16:42:22 muecker-dt kernel: [  658.940680] type=1503 audit(1257896542.578:26): operation="open" pid=4280 parent=4278 profile="/usr/sbin/mysqld-akonadi" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Nov 10 16:43:24 muecker-dt kernel: [  720.901126] evolution-excha[4463]: segfault at 10 ip 00007f9e308a5479 sp 00007f9e20e273e0 error 4 in libsoup-2.4.so.1.3.0[7f9e3087b000+4b000]
```

From syslog:
```

Nov 10 16:37:07 muecker-dt kernel: [  343.440449] evolution-excha[3905]: segfault at 10 ip 00007f9fecf4b479 sp 00007f9fddcce3e0 error 4 in libsoup-2.4.so.1.3.0[7f9fecf21000+4b000]
Nov 10 16:40:25 muecker-dt kernel: [  542.337921] evolution-excha[4180]: segfault at 7f750000000a ip 00007f7577d15eda sp 00007f75637fba90 error 4 in libc-2.10.1.so[7f7577ca0000+166000]
Nov 10 16:42:22 muecker-dt kernel: [  658.940680] type=1503 audit(1257896542.578:26): operation="open" pid=4280 parent=4278 profile="/usr/sbin/mysqld-akonadi" requested_mask="::r" denied_mask="::r" fsuid=1000 ouid=0 name="/sys/devices/system/cpu/"
Nov 10 16:43:24 muecker-dt kernel: [  720.901126] evolution-excha[4463]: segfault at 10 ip 00007f9e308a5479 sp 00007f9e20e273e0 error 4 in libsoup-2.4.so.1.3.0[7f9e3087b000+4b000]

```

Evolution was already unstable at best after I upgraded to Karmic, now it won't work at all!

I'm running Karmic with latest updates.  I typically run gnome, but I also installed kubuntu-desktop and sometimes run KDE.

---

### Post by muecker on 2009-11-11
The good news is I came in this morning and without any other changes was able to retrieve my email again.  I'm not sure what happened last night.

---

### Post by bcpayne on 2009-12-01
I get the same error but only when I enable my exchange calendar.  I can use my email fine (send, receive, etc) but as soon as I enable my calendar I loose connection with the exchange server; /var/log/messages has the following:

kernel: [90885.642216] evolution-excha[16377]: segfault at 0 ip b665bf43 sp b4bfe13c error 4 in libc-2.10.1.so[b65e9000+13e000]

Please advise.

Thanks,
Brent

---

### Post by combatkenpo66 on 2009-12-07
I've just started seeing this issue as well.  Any solution?

---

### Post by rrohbeck on 2010-01-05
This just happened to me too, but only on one machine, one of my first Karmic installs.
On two other systems, with the same configuration and the same Exchange account settings, it works fine.
I think on the system that doesn't work I used IMAP first and changed to Exchange later. Oh and it's also my slowest system (an EeePC 1005.)
I know some Evolution settings are stored outside ~/.evolution. If anybody has a complete list, I'll delete all of them, reinstall everything and see if that fixes it.

---

### Post by combatkenpo66 on 2010-02-15
Everything was good for about two months.  Anyone else having this same issue again?  Any ideas on how to fix it?

---

