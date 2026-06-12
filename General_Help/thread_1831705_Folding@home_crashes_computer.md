---
title: "Folding@home crashes computer"
date: 2011-08-23
forum: General Help
---

### Post by linuxman94 on 2011-08-23
As the title says, running folding@home always crashes Ubuntu when it gets to working the steps.  This occurs when using the smp flag on the client.  I tried removing smp and it worked, however it is slow and i can't take advantage of all 4 of my cores.  My hardware specs are in my sig.  At first i though it could be the memory, but after running memtest i get no errors.  This does not occur on windows vista, however that is 32bit not 64bit.  Any help is appreciated.

---

### Post by linuxman94 on 2011-08-25
BBBump

---

### Post by linuxman94 on 2011-08-26
Bump again.  Please tell me I'm not the only one with this issue.

---

### Post by linuxman94 on 2011-08-27
Bump

---

### Post by .... on 2011-08-27
Are you monitoring your CPU temp? I see you have your CPU OC'd, so does this happen at stock speed too? If not, you may need more voltage for the OC (or dial the speed back a bit).

---

### Post by linuxman94 on 2011-08-28
I monitor them temp, but it never goes over 55c.  And I'm 100% stable on the windows side.

---

### Post by .... on 2011-08-28
Linux probably gives the CPU a better multithreaded workout than Windows.

---

### Post by linuxman94 on 2011-08-28
Possibly, but I can run other cpu stress programs multithreaded with no problems

---

### Post by linuxman94 on 2011-08-29
Gah bump

---

### Post by .... on 2011-08-29
I would put the CPU at stock settings and see if the problem still occurs.

---

### Post by linuxman94 on 2011-08-30
It was the core clock.  I feel so stupid right now :lolflag:

Solved

---

