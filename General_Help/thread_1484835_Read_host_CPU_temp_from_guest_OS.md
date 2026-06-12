---
title: "Read host CPU temp from guest OS"
date: 2010-05-16
forum: General Help
---

### Post by karmic-koala on 2010-05-16
Is it possible to read the host cpu's temperature from a virtual guest? 

(1) Where host = ubuntu desktop and guest = ubuntu server, and
(2) Where host = windows xp and guest = ubuntu server?

Typically I would read the contents of /proc/acpi/thermal_zone/THRM/temperature
on host ubuntu desktop.

I guess its more tricky when running ubuntu on windows host. What I am trying to do is shutdown guest if host cpu temperature is greater than certain value.

Any ideas appreciated :)

---

### Post by lisati on 2010-05-16
Maybe I'm missing something here, but wouldn't they be the same physical CPU?

---

### Post by dcstar on 2010-05-16
[LIST=1]
[*]VMs run in an environment provided by the particular VM manager, direct host hardware resources are generally not available.
[*]Have the host run scripts to shut down VMs if there is a temp issue.
[*]What is wrong with posting VM questions in the Virtualization forum where the majority of people who know something about VMs are?
[/LIST]

---

