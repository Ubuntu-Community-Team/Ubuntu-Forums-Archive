---
title: "Sending output files to a different directory"
date: 2011-04-21
forum: General Help
---

### Post by salmontres on 2011-04-21
Hi all,

I'm running a program that periodically throws an out file in the directory where the executables are located. I'd like to pipe this output to a different directory automatically. Is there an easy way to do this? (I've tried looking it up online, but I only find commands that pipe the output from the terminal, which is NOT the case. The output is complete files.)

---

### Post by Krytarik on 2011-04-21
Is the name of those file always the same? If so, you can try creating a symlink there, pointing to the external file/location, and hope that your app doesn't delete it before saving the new file.

Hope it helps!

---

### Post by salmontres on 2011-04-21
Thanks for the quick reply Krytarik.

Unfortunately, the outfiles aren't named the same: they consist of names like wrfout_2011_4_20_12:00 and wrfout_2011_4_20_06:00. It's for a weather model. I'm using too much space on the supercomputer, so the administrators are going to stop allowing me to write to my directory. I wanted to send the output to the scratch space available. Essentially, I want to write a script that periodically checks my directory for a wrfout* file every hour or so. Any ideas how to continue?

---

### Post by Krytarik on 2011-04-21
> **salmontres said:**
> Essentially, I want to write a script that periodically checks my directory for a wrfout* file every hour or so. Any ideas how to continue?
For that you could create a simple crontab job:
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

