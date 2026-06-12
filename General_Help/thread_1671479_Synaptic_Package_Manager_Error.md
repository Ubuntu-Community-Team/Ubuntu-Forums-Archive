---
title: "Synaptic Package Manager Error"
date: 2011-01-20
forum: General Help
---

### Post by Shibbir on 2011-01-20
whenever i tried to open Synaptic package Manager the following messages shows:

[B]E: Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/B]

Ubuntu Software Center, Update Manager, Synaptic package Manager all are jammed and indicates the same error. Except these everything works perfectly.

How to fix this?? please please anyone help me..

---

### Post by plucky on 2011-01-20
> **Shibbir said:**
> whenever i tried to open Synaptic package Manager the following messages shows:

[B]E: Type '.net/tualatrix/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.[/B]

Ubuntu Software Center, Update Manager, Synaptic package Manager all are jammed and indicates the same error. Except these everything works perfectly.

How to fix this?? please please anyone help me..


Please post output from a terminal of ```
cat /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
``` as the list is incorrect.

---

### Post by oldos2er on 2011-01-20
```
gksu gedit /etc/apt/sources.list.d/tualatrix-ppa-maverick.list
```

Delete all the text, add these two lines:

deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) lucid main 
deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) lucid main 

Save and exit, run ```
sudo apt-get update
```

---

### Post by Shibbir on 2011-01-21
Thank you all for your valuable reply:popcorn:

I commented the two lines which indicates error. Now everything works again. But 
now there is another problem. when i tried this command: **"sudo apt-get update**". The updating process started and in 99% it says the following message:

[B]Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter[/B]

and every time i have to insert Ubuntu CD to continue. Any suggestion?? :D

---

### Post by plucky on 2011-01-21
> **Shibbir said:**
> Thank you all for your valuable reply:popcorn:

I commented the two lines which indicates error. Now everything works again. But 
now there is another problem. when i tried this command: **"sudo apt-get update**". The updating process started and in 99% it says the following message:

[B]Media change: please insert the disc labeled                                   
 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)'
in the drive '/cdrom/' and press enter[/B]

and every time i have to insert Ubuntu CD to continue. Any suggestion?? :D


Open Software Sources through Software Centre and un-tick the install  CDrom as a source.

Good Luck

---

### Post by Shibbir on 2011-01-21
@plucky: thanks bro. Now every thing works perfectly

Thanks again for your reply.

---

