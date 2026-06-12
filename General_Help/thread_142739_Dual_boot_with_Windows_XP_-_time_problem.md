---
title: "Dual boot with Windows XP - time problem"
date: 2006-03-11
forum: General Help
---

### Post by davidhong on 2006-03-11
Hi,

I have Ubuntu 5.10 with Windows XP. I have noticed that everytime Ubuntu boots up there are some activities going on with regards to system clock (UTC). And I have also enabled (in Ubuntu) synchronisation of clock using Ubuntu NTP servers. The time in Ubuntu is fine.

The problem is, when I boot Windows XP (after a successful shutdown of Ubuntu) the Windows time is set to wrong time. It's always GMT +21, when my original time is GMT +10. Only when I synchronise windows time, it come back to normal.

The problem is only there when Windows XP is booted after a successful Ubuntu session. If Windows XP is booted again after a successful Windows XP session - the problem does not exist.

I tried searching google as I remember seeing a similar post somewhere, but I just can't find it now when I need it the most.

---

### Post by twigboy on 2006-03-11
Because you dual boot with windows you arent suppose to synchronize with the ubuntu clock.  Once you disable that you should be good to go.

---

### Post by JoshHendo on 2006-03-11
Here is your problem...

Ubuntu sets the system clock to GMT, and then converts it live to your time format. Windows, just sets it to your time format, so in Windows your time will be in GMT. You have a few options.

1) Move to London
2) Set Ubuntu not to sync with the NTP servers
3) Live with it

Here is one that I reccoment. Stop it syncing. Set the correct time in Windows. Boot ubuntu, and change the time zone untill the time is correct. As it changes it live, it won't affect windows. That hopefully should work :)

---

