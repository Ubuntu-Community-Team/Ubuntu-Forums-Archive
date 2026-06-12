---
title: "How to reinstall unity after I've broken it"
date: 2012-01-11
forum: General Help
---

### Post by mind_master on 2012-01-11
Hello

I was messing with nvidia optimus things, and I decided to remove nvidia driver using "remove -purge nvidia*" and somehow ubuntu-desktop and maybe few others important packages were removed. Now when I log in in Unity I only see window menu at top and no launcher or indicators. 
How can I reinstall Unity?

P.S. writing this using GNOME3
P.P.S. ubuntu 11.10

---

### Post by Henkdroid on 2012-01-11
First I would recommend reinstalling any nVidia drivers using the proprietary drivers in the system settings, then open a terminal and type (when logged into a unity session) > unity --reset

---

### Post by mind_master on 2012-01-12
> **Henkdroid said:**
> First I would recommend reinstalling any nVidia drivers using the proprietary drivers in the system settings, then open a terminal and type (when logged into a unity session)

Thank you, it helped!
I've reinstalled ubuntu-desktop and then used "unity --reset". I didn't know about it before and tried to use "unity --replace".

P.S. I don't need nvidia drivers because I also have built-in intel graphics.

---

### Post by preschian on 2013-01-01
> **Henkdroid said:**
> First I would recommend reinstalling any nVidia drivers using the proprietary drivers in the system settings, then open a terminal and type (when logged into a unity session)

wow nice!

---

