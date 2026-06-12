---
title: "Can no longer &quot;Do nothing&quot; when laptop lid closes"
date: 2009-11-08
forum: General Help
---

### Post by Lokiii on 2009-11-08
Well, I just installed Ubuntu 9.10 on my laptop (which I use as a kind of server, sitting behind my TV). I have connected the laptop to my TV through HDMI and I wanted to make it so that if I close the laptop lid, nothing happens. However, that option is simply gone in the power settings menu. 

Now I can only choose Shutdown/Hibernate/Suspend or Blank Screen. However, the Blank screen option also affects my TV, leaving me with a nice black screen...

Help?

EDIT: Ive solved it. Cant figure out why on earth that option was removed.. Here is the solution:

In a terminal (Applications-->Accessories-->Terminal), type: gconf-editor

Navigate to apps-->gnome-power-manager-->buttons and set lid_ac and/or lid_battery to "nothing" (without the quotes).

---

### Post by bmcc618 on 2009-11-12
Hi, I followed these steps, however, "Do Nothing" does not appear in my power manager settings. I've rebooted also, no change. What gives?

---

### Post by eimme on 2009-11-12
> **bmcc618 said:**
> Hi, I followed these steps, however, "Do Nothing" does not appear in my power manager settings. I've rebooted also, no change. What gives?
I don't think its meant to appear in the setting with the above workaround. It should however set it to do nothing when closing the lid.

---

### Post by jgbelacqua on 2009-11-24
Another way to solve this, if all else fails, is documented here:
[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/49521)
The #22 reply solved my problem.  Going through the settings in gconf-editor also worked, but (for me) was slower to implement and test.

---

### Post by yoasif on 2009-11-24
Lokii, you should file your issue as a bug at: [https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-power-manager](https://bugzilla.gnome.org/enter_bug.cgi?product=gnome-power-manager) for gnome-power-preferences, so that other users do not have to edit a gconf setting.

---

### Post by 601 on 2010-02-06
Thanks Lokiii for the solution to this. Don't know if it helps anyone else (since it's a rather old thread) but on the current 9.10 ubuntu, I was able to set the option to do nothing and it does appear in the power manager settings too.

---

### Post by thecliff on 2010-02-06
Resolved the issue :D

---

### Post by carlos_listas on 2010-03-11
This workerd for me.

Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

Linux hp-dv1220us 2.6.31-20-generic #57-Ubuntu SMP Mon Feb 8 09:02:26 UTC 2010 x86_64 GNU/Linux

---

### Post by sunilsp on 2010-07-26
Excellent solution . Worked for me. Saves me the frustration

---

### Post by sriram.venkataramani on 2010-07-31
> **sunilsp said:**
> Excellent solution . Worked for me. Saves me the frustration

This is still an issue in 10.04 Netbook Edition. The workaround was fine, but can we add this as a bug?

---

### Post by jpr0 on 2010-08-26
Thank you! It works. (Asus laptop running Ubuntu 10.04 )

---

### Post by teachop on 2010-09-11
This problem is still in the maverick beta, and the fix still works.

---

### Post by gthm159 on 2011-03-17
Thank you Lokii for the workaround.

Here's the bug to track this issue:
[https://bugs.launchpad.net/bugs/736606](https://bugs.launchpad.net/bugs/736606)

- Googie

---

### Post by Xpistos on 2011-06-22
Believe it or not I just had this problem in 11.04 but thanks to Loki, the fix in gconf-editor did the trick. For me it is mandatory cause I can buy a new laptop and my screen is out so I need to shut the lid to see my external!

Efharistow (Greek for thank you.)

---

### Post by dandandrums on 2011-08-10
trick works in 11.04, thanks!

---

### Post by skippycostin on 2011-09-06
> **Lokiii said:**
> Well, I just installed Ubuntu 9.10 on my laptop (which I use as a kind of server, sitting behind my TV). I have connected the laptop to my TV through HDMI and I wanted to make it so that if I close the laptop lid, nothing happens. However, that option is simply gone in the power settings menu. 

Now I can only choose Shutdown/Hibernate/Suspend or Blank Screen. However, the Blank screen option also affects my TV, leaving me with a nice black screen...

Help?

EDIT: Ive solved it. Cant figure out why on earth that option was removed.. Here is the solution:

In a terminal (Applications-->Accessories-->Terminal), type: gconf-editor

Navigate to apps-->gnome-power-manager-->buttons and set lid_ac and/or lid_battery to "nothing" (without the quotes).

Thanks very much! Worked on my laptop running natty.

---

