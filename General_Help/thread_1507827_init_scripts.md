---
title: "init scripts"
date: 2010-06-12
forum: General Help
---

### Post by Enthrall on 2010-06-12
What exactly are they? Why wouldnt someone just add programs to ubuntus startup instead of using a script?

Im configuring deluge and to have the web ui and daemon run at boot I added them to startup and they are working fine. What are the advantages? Im new to all this.

---

### Post by Enthrall on 2010-06-12
anyone?

---

### Post by diesch on 2010-06-12
Init scripts (and upstart jobs) are run at boot and shut down time to start and stop services  before user login takes place. That's usually done for services that don't belong to any special user but are some sort of "system services" and may require root privileges to get started or stopped.

Programs that belong to some user (like Deluge) are usually better started at that user's session startup

---

