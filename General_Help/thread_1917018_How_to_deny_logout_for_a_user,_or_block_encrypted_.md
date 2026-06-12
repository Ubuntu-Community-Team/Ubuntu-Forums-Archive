---
title: "How to deny logout for a user, or block encrypted home directory unmount?"
date: 2012-01-29
forum: General Help
---

### Post by Artif on 2012-01-29
I have laptop with encrypted home directory. While backup to external stationary storage I want to have my "plain" files to be accessible to backup utility. At log off home directory become unmounted and turned to be a set of encrypted blobs.

Shutdown and reboot are not a problem - I blocked them via consolekit (see 'man pklocalauthority' and [http://askubuntu.com/questions/93542/how-to-disable-shutdown-reboot-suspend-hibernate/93956#93956](http://askubuntu.com/questions/93542/how-to-disable-shutdown-reboot-suspend-hibernate/93956#93956) ) and automated lock's up and down along with backup utility start and stop. And this do not lock down logoff process.

Can't find a way to control logout. I'm familiar with shell scripting, I think I can automate most of logout denial ways, but I don't know any ways to do a logoff hook.

**How to intercept logout tries or events and block them?**

I'm afraid a ways to control accessibility via control of encrypted directory mount point can lead to unavailability of computer until backup's finish. I.e. logout may pause at the middle and wait for backup. Am I right?

---

