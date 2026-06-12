---
title: "Looking for an easier way to update source.list after release upgrade"
date: 2011-04-26
forum: General Help
---

### Post by Chaconne on 2011-04-26
Hi, all,

Is there an easier way to update source.list after upgrading to a new release?

Until now, each time I upgraded to the new release, all third-party software sources were commented out automatically during the OS release upgrade. After the new version was up and running, I had to manually edit each line to re-enable the sources. The true nuisance is that not every source has the latest release directory available, which means I have to check one by one each source to ensure the validity of my modification. I'd really like a more intelligent and less tedious way to update the source.list given that 11.04 upgrade is around the corner. Thanks in advance.

---

### Post by wolfen69 on 2011-04-26
You can do it through synaptic (GUI).

---

### Post by Chaconne on 2011-04-27
Hi, wolfen69,

Thanks for the reply. Could you please elaborate a little though on how to update the source.list through synaptic? I'm too nooby to find the right button.

---

### Post by wolfen69 on 2011-04-27
In synaptic, go to settings-repositories-other software and check off what you want enabled.

---

### Post by Chaconne on 2011-04-27
Hi, wolfen69,

According to my understanding, it is basically bringing you to the GUI interface of software source. By ticking the boxes, you enable the sources, but will the source be updated automatically to the directory of the new release? For example, when I upgraded from lucid to maverick, all third party sources were disabled by the upgrade process. After I re-enabled the sources, they were still pointing to lucid directory as before the upgrade. I had to edit each software source to re-point them to maverick directory so that the related software could be updated properly. Meanwhile, I had to make sure the new natty directory did exist. Can these steps be accomplished automatically?

---

