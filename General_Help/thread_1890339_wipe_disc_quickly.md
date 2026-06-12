---
title: "wipe disc quickly"
date: 2011-12-03
forum: General Help
---

### Post by Mappenz on 2011-12-03
Hi,

i want to wipe my disc for sale. I found that ```
dd if=/dev/zero of=/dev/sda
``` does this. But dd is running for hours now. Is there a quicker way?

---

### Post by MG&amp;TL on 2011-12-03
If you just want any sensitive data removed, I imagine "boot and nuke" will do the trick. Just make sure you haven't got anything else plugged in.

[http://www.dban.org/]("http://www.dban.org/")

---

### Post by Serpher on 2011-12-03
If you want your data gone for GOOD use that dd command. It has to manually set each bit on that harddisk to a 0. A bit for bit copy of a hardrive using 'dd' can hold up in court.

---

### Post by CharlesA on 2011-12-03
> **MG&TL said:**
> If you just want any sensitive data removed, I imagine "boot and nuke" will do the trick. Just make sure you haven't got anything else plugged in.

[http://www.dban.org/]("http://www.dban.org/")

dd can do a similar thing.

> **Serpher said:**
> If you want your data gone for GOOD use that dd command. It has to manually set each bit on that harddisk to a 0. A bit for bit copy of a hardrive using 'dd' can hold up in court.

Yeah. But it takes a super long time.

If you want your data destroyed there is no "quick and dirty" way of doing it unless you smash the platters themselves.

---

### Post by The Cog on 2011-12-03
I hope you are doing this from a live CD. If you're doing it from the OS that you are wiping, it's possible the OS has crashed and isn't doing anything any more.

It is normal for a dd disk wipe to take a long time.

---

### Post by Mappenz on 2011-12-03
Yes, i use a live cd. I also get some unreadable output indicating that the system is still running. I found that the parameter bs could speed up the process. But i dont know if it wasnt done in a minute anyway. Maybe boot and nuke was a good idea.

---

### Post by Serpher on 2011-12-03
> **Mappenz said:**
> Yes, i use a live cd. I also get some unreadable output indicating that the system is still running. I found that the parameter bs could speed up the process. But i dont know if it wasnt done in a minute anyway. Maybe boot and nuke was a good idea.

I wouldn't use those parameters. If it's speeding it up some bits aren't being reset. That nuke software probably works but if you want things 100% wiped in every way shape and form, just run the command you posted in the OP and do something else for a while xP.

---

### Post by dcstar on 2011-12-04
> **Mappenz said:**
> Hi,

i want to wipe my disc for sale. I found that ```
dd if=/dev/zero of=/dev/sda
``` does this. But dd is running for hours now. Is there a quicker way?

Yes:

[http://tinyapps.org/docs/wipe_drives_hdparm.html](http://tinyapps.org/docs/wipe_drives_hdparm.html)

---

### Post by cap10Ibraim on 2011-12-04
if you interrupt dd now , you may get your self some bad sectors and then your disk will not be for sale any more :)

---

### Post by Mappenz on 2011-12-04
Its still running, I need to travel soon. Since I think vibrations should be very bad for a hard drive during a writing operation I am not sure whether its better to stopp dd or keep it running.

---

### Post by The Cog on 2011-12-04
That is taking longer than I would expect. You can interrupt dd - just Ctrl-C out of it. But you won't know how much of the disk was wiped.

---

