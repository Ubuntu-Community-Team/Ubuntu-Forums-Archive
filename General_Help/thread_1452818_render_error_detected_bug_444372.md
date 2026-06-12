---
title: "render error detected bug 444372"
date: 2010-04-12
forum: General Help
---

### Post by trouts2 on 2010-04-12
I think I have Bug #444372 which seems to be fixed and available.

    I have installed Ubuntu 9.10 \n \l Linux 2.6.31-20generic #58-Ubuntu SPM Fri Mar 12 i686 GNU

This was listed as fixed 2010-02-10
and
Bug Watch Updater on 2010-03-02 Changed in linux: 
status: 	Confirmed &#8594; Fix Released

I installed 9.10 by ISO DVD gotten from the Ubuntu website after 2010-03-02.  I have installed all updates in the Update Manager today.  

The error output is still showing up in my syslog:
render error detected, EIR: 0x00000010
[drm:i915_handle_error] error EIR stuck: 0x00000010, masking
render error detected, EIR: 0x0000010

The question is should the updating have loaded the fix?

My system hangs frequently. The desktop looks normal and the mouse is alive but nothing on the desktop will respond.  CTL ALT F2 does not respond.  I'm not sure if this bug is related.

My hardware is an emachine D2823 Celeron D 325 with 256MB.  Not the best and I expect it to be slow but not hang forcing a plug pull.

---

### Post by WinterRain on 2010-04-12
Sounds like it could be hardware related. Have you done any diagnostics such as memtest?

---

### Post by trouts2 on 2010-04-12
No errors reported from memtester.
The system runs fine under heavy load with XP.

---

