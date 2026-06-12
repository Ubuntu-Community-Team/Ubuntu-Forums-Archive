---
title: "Where is System Info?"
date: 2006-02-02
forum: General Help
---

### Post by fishmorg909 on 2006-02-02
I can't find the info about my system -- not in System Monitor, not in Device database... you know, the stuff about your computer, its speed, memory, etc., etc.... silly question, but I've made searches here in the forums, and I still don't know! :confused:

---

### Post by siucdude on 2006-02-02
well i use something called "hardinfo"  go to synaptic and install it search "hardinfo" should display and then after install shows up in apllications system tools.  give that a try

---

### Post by ZylGadis on 2006-02-02
In terminal:

cat /proc/cpuinfo
cat /proc/meminfo

That should be plenty for the cpu and memory. You can also try System -> Administration -> Device Manager for general information on the hardware in your box.

---

### Post by ekarni on 2006-02-02
Also try the command  lshw

---

### Post by fishmorg909 on 2006-02-02
[QUOTE=siucdude]well i use something called "hardinfo"  go to synaptic and install it search "hardinfo" should display and then after install shows up in apllications system tools.  give that a try[/QUOTE]

Thanks all, especially siucdude -- hardinfo was just the thing. Worked great the first time! :D

---

