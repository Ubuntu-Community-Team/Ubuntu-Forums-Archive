---
title: "Office"
date: 2011-06-09
forum: General Help
---

### Post by TimeWillShow on 2011-06-09
Oke I dont know if I am placing this post in the right forum, but I really need some help on this, so please be forgiving:p

I am a windows user that tries to make the step to ubunut!:p

For me it must make sense to step to ubuntu so I want to go hardcore open source. Now I need an office app that actually works, i have tried libreoffice and openoffice. The problem is not the fact that it is not as good as Microsoft office (i can live with that), but my biggest problem is that if someone sends me an Microsoft office file my libreoffice goes nuts! the layout is not what it has to be and so on and so on.

I have read on forums and blogs that this is something that we cant solve. I haven't found anything positive on these forums and blogs, so I thought you guys could help me!

I don't want to install microsoft office on my ubuntu, because that would make no sense at all!

So is there someone who knows a trick? I really need to be able to function on this thing!

ohh I also tried the cloud (google documents) it has the same problem, why the hell do they all have the layout problem?

---

### Post by idoitprone on 2011-06-09
It is a problem with proprietary formats. Microsoft doc format changes with every revision of microsoft office. Blame microsoft. It more of a vendor lock in devised by Microsoft themselves. To make matters worse, if hackers add support to the open source alternatives, then microsoft might sue for patent infrigement or whatever. Both libreoffice, openoffice, and google docs use open document format, although google might store the office document in their own format to save space. I afraid libreoffice the best alternative out there. I believe it should have some support for docx in microsoft office 2007.
[http://www.libreoffice.org/features/writer/](http://www.libreoffice.org/features/writer/)
 If you are have trouble then you may be using the newest microsoft doc format which is from 2010.

try to ask you co worker to save in docx 2007 format.

from the looks of it, only office 2007 remotely works

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=31](http://appdb.winehq.org/objectManager.php?sClass=application&iId=31)

---

### Post by linuxinstalledfromhdd on 2011-06-09
> **TimeWillShow said:**
> Oke I dont know if I am placing this post in the right forum, but I really need some help on this, so please be forgiving:p

I am a windows user that tries to make the step to ubunut!:p

For me it must make sense to step to ubuntu so I want to go hardcore open source. Now I need an office app that actually works, i have tried libreoffice and openoffice. The problem is not the fact that it is not as good as Microsoft office (i can live with that), but my biggest problem is that if someone sends me an Microsoft office file my libreoffice goes nuts! the layout is not what it has to be and so on and so on.

I have read on forums and blogs that this is something that we cant solve. I haven't found anything positive on these forums and blogs, so I thought you guys could help me!

I don't want to install microsoft office on my ubuntu, because that would make no sense at all!

So is there someone who knows a trick? I really need to be able to function on this thing!

ohh I also tried the cloud (google documents) it has the same problem, why the hell do they all have the layout problem?

You can install an older version of Office on Ubuntu, like Office 2003, and it works great with PlayOnLinux:

[http://cinderbox.net/2011/05/23/2856/](http://cinderbox.net/2011/05/23/2856/)

Or you can install VMware:

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

There are so many options available for you to make your transition really comfortable. And that way you can go at your own pace.  Here is a guide to getting a system started. I recommend 10.10:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by idoitprone on 2011-06-10
> **linuxinstalledfromhdd said:**
> You can install an older version of Office on Ubuntu, like Office 2003, and it works great with PlayOnLinux:

[http://cinderbox.net/2011/05/23/2856/](http://cinderbox.net/2011/05/23/2856/)
i dont think that would work, since office 2003 cannot support the newer doc formats. It only works up to 2007 with a plugin which libreoffice supports
Oh well, I am not sure 2010 works

> Or you can install VMware:

[http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/](http://cinderbox.net/2011/06/08/how-to-run-windows-in-ubuntu-with-vmware-player/)

Virtualbox is another alternative to vmware

---

### Post by linuxinstalledfromhdd on 2011-06-10
> **idoitprone said:**
> i dont think that would work, since office 2003 cannot support the newer doc formats. It only works up to 2007 with a plugin which libreoffice supports
Oh well, I am not sure 2010 works



Virtualbox is another alternative to vmware

The way I had it for a while when I was first starting out was using VMware with WinXP and the latest Office Suite, and I created a shared folder within Ubuntu to save my work. Eventually I migrated everything slowly over to OpenOffice which is now LibreOffice.  I rarely would need to use it now. :)

---

