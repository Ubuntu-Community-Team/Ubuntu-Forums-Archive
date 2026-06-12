---
title: "Message on Shutdown?"
date: 2011-11-09
forum: General Help
---

### Post by cancer10in on 2011-11-09
Hi

I am using ubuntu 10.04. Is there anyway we can display a custom message when shutting down the machine?


Any help will be appreciated.


Thanks

---

### Post by dcstar on 2011-11-10
> **cancer10in said:**
> Hi

I am using ubuntu 10.04. Is there anyway we can display a custom message when shutting down the machine?
......

Doubtful, the "fast shutdown" procedure tries to kill off things ASAP and it has proved tricky to get in its way.

You can try putting scripts that are run in the /etc/rc0.d (shutdown scripts) & rc6.d (reboot scripts) folders and see if that works for you.

---

### Post by cancer10in on 2011-11-10
> **dcstar said:**
> Doubtful, the "fast shutdown" procedure tries to kill off things ASAP and it has proved tricky to get in its way.

You can try putting scripts that are run in the /etc/rc0.d (shutdown scripts) & rc6.d (reboot scripts) folders and see if that works for you.


What would that script contain? Do you have a sample?

---

