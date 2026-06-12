---
title: "Overclocking question (CPU governor related)"
date: 2012-07-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-07-16
I am considering modestly overclocking my CPU (like 2 to 4 hundred MHz)
If I do will it add a new governor or replace my highest one (3.4GHz) I would rather it not use it unless a process actually needs the extra power and not just cause 2.7Ghz is not enough

cooling is not a issue, temps are below 45C with under 50% fan speed at max load for over 14min

---

### Post by 3Miro on 2012-07-16
I think you are confusing the meaning of the word "governor". The CPU/BIOS reports a list of available frequencies and then the Linux kernel selects from those frequencies according to an algorithm, which is called "governor". For example, governor performance would always select the highest frequency. Governor ondemand would select the lowest and if a process uses a lot of power, then the CPU will change to the highest frequency.

If you overclock, you should simply see a higher value for the maximum frequency and the default governor (ondemand unless you changed it), will select the highest frequency when needed.

---

