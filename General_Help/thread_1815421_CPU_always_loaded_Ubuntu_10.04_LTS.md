---
title: "CPU always loaded Ubuntu 10.04 LTS"
date: 2011-07-31
forum: General Help
---

### Post by Gemu on 2011-07-31
Does anyone have a clue why my CPU monitor all the sudden stays half colored. It just started doing this a couple of days ago. The computer never rests it constantly has a load on it and the fan runs on high. 

Thanks for any help

---

### Post by coffee412 on 2011-07-31
> **Gemu said:**
> Does anyone have a clue why my CPU monitor all the sudden stays half colored. It just started doing this a couple of days ago. The computer never rests it constantly has a load on it and the fan runs on high. 

Thanks for any help

When ever I have a situation like this I open up a term window and type in "top" and hit enter. This will show you the processes and how much memory and cpu time they are taking up. From there you can discover the offending process.

coffee

---

### Post by Gemu on 2011-07-31
> **coffee412 said:**
> When ever I have a situation like this I open up a term window and type in "top" and hit enter. This will show you the processes and how much memory and cpu time they are taking up. From there you can discover the offending process.

coffee

It looks like a program called kaspid is hogging 95 CPU's. How do I kill it? ti just started this after the last update on my computer.

---

### Post by coffee412 on 2011-07-31
> **Gemu said:**
> It looks like a program called kaspid is hogging 95 CPU's. How do I kill it? ti just started this after the last update on my computer.

sudo killall kaspid

---

### Post by Gemu on 2011-07-31
That doesn't seem to get it done. The actual process is called kacpid

---

### Post by lithopsian on 2011-07-31
k-acpi-d.  You want this, but something is obviously wrong.  Might be missing modules or an ACPI configuration problem.

It won't be easy to kill since it is likely to be running as root and will probably ignore anything except a kill -9.

---

### Post by Gemu on 2011-08-01
I hope I find a way to kill it soon, its weighing my computer down tremendously. I have a good fast 3000 mhz computer and its frustrating to be using 78% CPU before I open any pages. Another one right beside it is kacpi_notify but it only runs about 4% CPU. kacpi uses 94 to 95 % according to htop.

---

