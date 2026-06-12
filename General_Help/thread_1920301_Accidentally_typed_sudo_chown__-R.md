---
title: "Accidentally typed sudo chown / -R"
date: 2012-02-04
forum: General Help
---

### Post by 51B0RG on 2012-02-04
i accidentally typed in sudo chown / -R and now everything has gone to hell!

i was trying to do sudo chown /var/www -R

im using ubuntu server 11.10 x64 with i386

i have a ton of stuff on my server i cannot lose any of it!

---

### Post by ajgreeny on 2012-02-04
Oh boy!  That will make life difficult, to say the least.

You may be able to get back to a more standard setup by rebooting to recovery mode from the grub menu (hit and hold shift at poweron if you don't normally see the grub menu) and from there, assuming it boots OK, you may be able to run ```
chown -R *username*:*username* /home/*username*
```Change username to whatever the usual user account is named on the server.

I think that the /home/username will be the only folder that has changed ownership, as everything else would already be owned by root, I think, and that command ought to return ownership of the home/username folder to your user, as it should be.  Even if you did end up having to reinstall, there is no reason why you should lose any files, as you can always get them back with a live CD.

---

### Post by squenson on 2012-02-04
> **51B0RG said:**
> i have a ton of stuff on my server i cannot lose any of it!This is why it is important to perform regular backups. The frequency of these backups should be proportional to the amount of data you are ready to lose and the effort to recreate/recover them.

---

