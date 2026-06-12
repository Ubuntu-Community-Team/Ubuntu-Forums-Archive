---
title: "GDM error"
date: 2010-01-24
forum: General Help
---

### Post by alflavor on 2010-01-24
Hi all I'm new to Ubuntu, well have dabbled before, but now want to get to grips with Linux on my netbook. Went for a re-bbot to keep the wife happy who likes Windows.

So once I had partitioned and installed from USB I rebooted, the Ubuntu splash screen appeared and then an error:

Server Authorisation Directory (daemon/ServAuthDir) is set to /var/lib/gdm but is not owned by user 105 and group 111. Please correct the ownership or GDM configuration and restart GDM.

I can F2 into the console, and can login to the CLI with username and password I set at install.

However then pops up *stopping anac(h)ronistic cron anachron.

I've tried sudo chown gdm:gdm /var/lib/gdm
and then a reboot but the same happens.

Can anyone point me in the right direction?
Thanks
Al

---

