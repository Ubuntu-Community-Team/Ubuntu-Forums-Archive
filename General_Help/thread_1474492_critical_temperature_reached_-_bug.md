---
title: "critical temperature reached - bug"
date: 2010-05-06
forum: General Help
---

### Post by vladimirk on 2010-05-06
Hi!

After the latest update I got this error during the boot:  critical temperature reached (121 C) shutting down.

But BIOS shows CPU temperature 50C (122F).

It looks like ubuntu mixed up C with F.
Is there any way to turn-off auto shutdown? Or increase threshold temperature?

PS ubuntu 10.4, kernel 2.6.32

---

### Post by 3rdalbum on 2010-05-06
The BIOS shows the temperature after the shutdown has occurred. As soon as the CPU is turned off, the temperature starts dropping at a rapid rate.

---

### Post by vladimirk on 2010-05-06
problem was solved.

in my system installed not default CPU fan without 3rd pin, so bios shows 0 rmp for this fan
somehow in bios was set to shutdown system if CPU fan fails.
So I unchecked this option and system works fine.

But CPU temperature always was stable near 50C.
So ubuntu  shows wrong message, instead CPU fan fails it shows false CPU overheating (121 C)

---

