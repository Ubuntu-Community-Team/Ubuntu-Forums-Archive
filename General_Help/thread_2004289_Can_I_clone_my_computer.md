---
title: "Can I clone my computer?"
date: 2012-06-15
forum: General Help
---

### Post by AlexBooton on 2012-06-15
Hi,

I'd like to prepare a complete backup of my U12.04 server.

If I back up everything (i.e. /*.*) to an external drive can I simply copy it back to the new server?  

The system I want to use as the clone currently has U11.04.

I realize there are some hardware differences which I think I'd be able to fix up after the new clone is active.  Some of the hardware is different; they two machines will need different IPs; the server name will have to be changed; etc.

But will all packages be automatically set up by the cloning process?  Will tar preserve owners and permissions?

Do you think this will work?

Is there a better way?

Thanks,

AB

---

### Post by MG&amp;TL on 2012-06-15
I think [http://www.remastersys.com/](http://www.remastersys.com/) is what you're after. It makes an iso from your system, but  makes an installer too. So you can just copy it across.

---

### Post by quadproc on 2012-06-15
> **AlexBooton said:**
> Hi,

I'd like to prepare a complete backup of my U12.04 server.

If I back up everything (i.e. /*.*) to an external drive can I simply copy it back to the new server?  


You probably need to do some studying on the duplicating issue.  For example, the specification "*.*" will only match files that include a . in the file name.

One thing to look at is clonezilla - it will duplicate exactly a disk onto another disk, including things such as UUIDs and boot records.

quadproc

---

### Post by AlexBooton on 2012-06-15
> **quadproc said:**
> You probably need to do some studying on the duplicating issue.  For example, the specification "*.*" will only match files that include a . in the file name.

One thing to look at is clonezilla - it will duplicate exactly a disk onto another disk, including things such as UUIDs and boot records.

quadproc

Thanks, I'll take a look at clonezilla.

AB

---

