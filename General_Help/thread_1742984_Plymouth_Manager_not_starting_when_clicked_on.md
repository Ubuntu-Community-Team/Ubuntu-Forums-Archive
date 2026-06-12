---
title: "Plymouth Manager not starting when clicked on"
date: 2011-04-29
forum: General Help
---

### Post by RichieB07 on 2011-04-29
I installed Plymouth Manager a while ago and have had no problems with it until now.  I want to change my splash screen (it's currently set to the Macbuntu one), but it won't start up when clicked on.  I have the Screenlet Sysmonitor, and it doesn't even show the process as starting when clicked on as if I did nothing.

Running Ubuntu 10.10, Acer Aspire 5520.

---

### Post by RichieB07 on 2011-04-30
Update on this:

I went into Synaptic to just do a reinstall, but that option wasn't available.  So I uninstalled it thinking I'd just reinstall.  Now it's not even showing up in Synaptic at all.

When I run

```
sudo apt-get install plymouth-manager
```it shuts down the terminal.


Any ideas?

---

### Post by RichieB07 on 2011-05-24
I just ran this today to see if it had fixed.  Now it says it can't find "plymouth-manager" but at least the terminal doesn't shut down.

[IMG]http://i51.tinypic.com/ousgom.png[/IMG]

---

### Post by linuxinstalledfromhdd on 2011-05-24
Contact the support group, mailing list or whatever,  for the PPA that you installed on your system.  If you didn't use a PPA to install it, uninstall the manager and reset plymouth to the default screen.  Also you can uninstall the macbuntu with the uninstall.sh that was originally provided with that compressed file.  Or you download it again and extract everything to have that script to use to uninstall it. Macbuntu should reset it.

---

### Post by RichieB07 on 2011-05-25
I found the way to manually reset it online and use that now, and have actually reinstalled Macbuntu before.  It didn't fix it; just seems odd to me.

---

### Post by linuxinstalledfromhdd on 2011-05-25
I would imagine that the uninstall script provided with Macbuntu would provide a way to rollback the plymouth splash to it's pre-installation setting and display it normally with the Ubuntu logo and little dots.  Hmmmm:confused:

---

### Post by RichieB07 on 2011-05-25
You would imagine but now that I can't even get the manager to even be found, it's a little confusing.

---

### Post by LordNeo on 2011-05-25
Check this:

[http://ubuntu-tweak.com/source/mefrio-g-plymouthmanager/](http://ubuntu-tweak.com/source/mefrio-g-plymouthmanager/)

Install the PPA and install plymouth manager from there. It should solve your issue and let you change your plymouth again

PD: Just for future reference the PPA instruction is: sudo add-apt-repository **ppa:mefrio-g/plymouthmanager**

---

### Post by RichieB07 on 2011-05-26
Thanks.  I actually installed it from Synaptic I do believe, so it's weird that it's gone now.

But I'll definitely give those a try to see if it works.

---

