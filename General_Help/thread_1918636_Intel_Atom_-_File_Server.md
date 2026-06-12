---
title: "Intel Atom - File Server?"
date: 2012-02-01
forum: General Help
---

### Post by Roasted on 2012-02-01
I have a file server just for home storage that I throw Deja Dup backups at daily. I also have a few family members who back up to it as well via SSH from their house to mine. My file server is Ubuntu running on a 4gb flash drive and a pair of 500gb MDADM software raid 1 drives.

Would an Intel Atom work okay for this? I keep thinking the Pentium Dual Core I have in there is a bit overkill. Considering I have uses for the Pentium Dual Core elsewhere and I wouldn't mind using as low wattage as possible for my file server consumption, that's the idea on the table.

Worth it?

---

### Post by CharlesA on 2012-02-01
An Atom is fine if all you will be doing is serving files.

---

### Post by bewarellamas on 2012-02-01
I do basically the same thing but with FreeNAS on an Atom board with no troubles. I think the Atom would handle it just fine.

---

### Post by Khayyam on 2012-02-01
Roasted ...

I would say the Atom is overkill, heh. I've used various PII's (300mhz, 256mb RAM) for this purpose and they perform just fine, the NIC and/or router will be more of an issue than the fileservers processor. So, besides the issue of power consumption, you could replace it with something even less substancial than an Atom.

HTH ...

---

### Post by Roasted on 2012-02-01
I might have to re-visit this thought process a bit. I also use ZoneMinder on my file server and record a home surveillance stream from a wifi camera outside. If I recall pulling a consistent camera feed is quite taxing on a system. I think that may be why I had gone with a low end dual core to begin with.

With the new-found information above, any further opinion about it? I suppose I could set up ZoneMinder on my netbook and see how it works as a test...

---

### Post by CharlesA on 2012-02-01
I'm not sure how much that would tax the machine, but you can always try it on your netbook and see what happens.

Worse case is that it won't work.

I wonder if a dual core atom would work for that.

---

