---
title: "Xen vs. vmware"
date: 2006-06-03
forum: General Help
---

### Post by leetcharmer on 2006-06-03
Which would you pick and why?

---

### Post by leetcharmer on 2006-06-04
lawl -- it's good that ya'll are voting .. VMware is ahead ... any explainations why you like it better though?

---

### Post by Eklöf on 2006-06-04
How do you install Xen for Dapper ?

---

### Post by henriquemaia on 2006-06-04
[quote=Eklöf]How do you install Xen for Dapper ?[/quote]

Maybe this is a good point on why VMWare is ahead.

---

### Post by charnov on 2006-06-04
Well, Xen requires a modified kernel which automatically gets a "no" from me, but it also is only a paravirtualization (kind of a time slice) and cannot handle corner cases. Not really usefull for a desktop distro (although this would be an interesting way to run 64 and 32 bit side by side...exactly the same method Microsoft uses for XP 64 bit).

VMWare is full virtualization of a platform with paravirtualization of the CPU (so only x86) and it can handle corner cases so full windows suppport, etc. Again, not that usefull for desktop distro unless you need true Windows compatibility or for learning, prototyping (thats what I use it for), etc.

I voted for VMWare due to wonderful support, corner case handling, ease of installation, and greater utility.

---

### Post by traherom on 2006-06-04
VMware, because Xen can't run anything but Linux.

---

### Post by garyng on 2006-06-04
It is a bit like apple vs orange to me. Xen is mainly used for partitioning a server into multiple linux/bsd instance. VMWare while also has this capability is more gear towards heterogenous(linux/windows etc.) Xen has a huge performance advantage so if I run a hosting service for linux, I would go for Xen.

There is actually another class, vserver/openvz which is even better than Xen in terms of performance loss(I think less than 2%).

I would say, different products for entirely different purpose.

BTW, Xen if running on VT enabled hardware can run Windows unmodified if memory serve. So on VT enabled hardware, Xen and VMware will become more a like feature and peformance wise. It would then boil down to cost(free for Xen) vs management interface(more mature in VMWare).

---

### Post by nix4me on 2006-06-04
I voted vmware beacuse its here already and its easy to install and it works.

nix4me

---

### Post by QUASAR_FREAK on 2006-06-04
I choose Xen because is opensource but vmware actually run ok in my pc and its much easier to configure.

---

### Post by jimcooncat on 2006-06-04
Vmware for now. I'll go with Xen when:

[LIST]
[*]It's easy to buy an AMD system with Pacifica
[*]Support is included with Ubuntu's default kernel
[*]Documentation doesn't require a CS degree to understand
[/LIST]

oh yeah:

[LIST]
[*]and a pony!
[/LIST]

---

### Post by AndyCooll on 2006-06-04
I believe Xen has the "possibility" to be more efficient them VMware, but as an earlier poster mentions it seems to require a "CS degree" to understand the installation process.

Having said that this latest Ubuntu version of VMware Player I've just installed on Dapper is excellent. It's running my copy of XP without any noticeable slowness.

:cool:

---

### Post by djsroknrol on 2006-06-04
I'm with VMware...it's been a fine lad for me...

Hopefully, Xen will be in Edgy...or at least that's what Mark Shuttleworth is hoping for in the podcast I heard thru another post...

---

