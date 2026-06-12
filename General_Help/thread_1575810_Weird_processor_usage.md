---
title: "Weird processor usage"
date: 2010-09-16
forum: General Help
---

### Post by NertSkull on 2010-09-16
I put the system monitor (2.30.0) on my panel to watch CPU usage.

Sometimes (probably once or twice a week) it will tell me that it is using 40-60 % of my processor.

But if I go to a terminal and use top (or htop) it tells my only 3% or so is being used.

Why the discrepancy? It's slightly concerning to me one things says my computer is doing lots of stuff, while another says its not.

---

### Post by ngrieb on 2010-09-16
Do you have more than one core or thread? Are you accounting for the resources that the system monitor itself uses?

---

### Post by NertSkull on 2010-09-17
I have two cores. (I don't know enough to know how many threads)  

But htop will separate that out and say how much each is using, usually its like 3% and 6% or something.  And in the list it shows the system-monitor process.  So it does take that into account.

The system-monitor on the panel however does not seem to divide (at least that I can tell) into the two cores.  It just has one %.  But it does list the resources being used by system-monitor.

In both cases the resources used by system monitor come no where near what the panel says the processor is using.

---

