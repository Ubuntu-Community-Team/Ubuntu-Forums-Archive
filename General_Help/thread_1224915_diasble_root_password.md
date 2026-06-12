---
title: "diasble root password?"
date: 2009-07-27
forum: General Help
---

### Post by abhilashm86 on 2009-07-27
i'm working alone in my computer, no other user uses, as its threat having root password, i want to disable it.......
what are your suggestions? shall i keep it or delete, i just use sudo and not root password, i want to safely remove root password, how to do it?

---

### Post by philcamlin on 2009-07-27
sudo passwd -l root

:)

---

### Post by lisati on 2009-07-27
The root account is disabled by default with Ubuntu - I'd suggest retaining sudo for administrative purposes.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by abhilashm86 on 2009-07-27
> **lisati said:**
> The root account is disabled by default with Ubuntu - I'd suggest retaining sudo for administrative purposes.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

yea i want to retain sudo, i actually made another password for root by using this some months before ```

sudo passwd root 

```
this is the one i need to delete, i saw a video somewhere, if you keep root password, one can hack password:) so i'm deleting it.........

---

