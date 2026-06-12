---
title: "upgrading ubuntu 10.04 problem"
date: 2011-01-17
forum: General Help
---

### Post by muhammad86 on 2011-01-17
hi
I have problem upgrading my ubuntu 10.04 lucid to a newer release of Ubuntu. I have done updates regularly but nothing prompt regarding upgrading Ubuntu.
as mentioned in Ubuntu website, updating must result in a notification of upgrading. I want to know if there is any way to do this manually?

---

### Post by mikewhatever on 2011-01-17
10.04 is an LTS version, and by default, an LTS would only be upgraded to an LTS. You can change it under System->Admin->SoftwareSources, Updates tab.

---

### Post by coffeecat on 2011-01-17
Open Update Manager and click on the 'Settings' button. In the Software Sources window that opens, click on the 'Updates' tab. Under 'Release upgrade' make sure 'Normal releases' is selected. It sounds as though you have long term support releases only selected.

---

### Post by muhammad86 on 2011-01-17
thanks for your responses. I changed the update setting and alter the upgrade section to normal releases. it worked, but[COLOR=Red] [SIZE=4]another problem happened. while upgrading was processed, an error occurred and when it was calculating changes it stopped and the process was aborted. I did not get what the problem was; is it related to LTS format of my release or it can be resolved? any one nay suggestion[/SIZE][/COLOR]

---

### Post by plucky on 2011-01-17
> **muhammad86 said:**
> thanks for your responses. I changed the update setting and alter the upgrade section to normal releases. it worked, but another problem happened. while upgrading was processed, an error occurred and when it was calculating changes it stopped and the process was aborted. I did not get what the problem was; is it related to LTS format of my release or it can be resolved? any one nay suggestion

Try disabling all third party repositories under the **Other Software** tab in **Software Sources** and try again.

Good Luck

---

