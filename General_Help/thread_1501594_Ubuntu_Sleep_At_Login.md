---
title: "Ubuntu Sleep At Login"
date: 2010-06-04
forum: General Help
---

### Post by dude378 on 2010-06-04
Hello,

I currently have a Windows 7 server set up in my home. All it does is share files with the entire network. So when no one is using it, I have it configured to go to sleep in 10 minutes. Then I can wake it back up over LAN.

With windows one of the problems was that it could not go to sleep at the login screen. So if it started from off or if it just woke up, it would show the login screen and just sit there. The only solution I found was to disable the password and allow auto login for both situations.

I'm wondering if Ubuntu can sleep at the login screen, or will I have to disable the password and login screen as well? If so, can the login screen actually be disabled when booting from off and also when recovering from sleep?

Also I'm assuming it has the option of sleeping if no one uses it for x-minutes, but can someone confirm that?


Thanks.

---

### Post by dcstar on 2010-06-05
> **dude378 said:**
> 
........
I'm wondering if Ubuntu can sleep at the login screen, or will I have to disable the password and login screen as well? If so, can the login screen actually be disabled when booting from off and also when recovering from sleep?

Also I'm assuming it has the option of sleeping if no one uses it for x-minutes, but can someone confirm that?


The only "sleep" is shutting down the monitor, you can have the screensaver kick in after a set time or just use the power manager to do this.

Performing as a fileserver is irrelevant to any display sleep setting.

---

### Post by dude378 on 2010-06-06
> **dcstar said:**
> Performing as a fileserver is irrelevant to any display sleep setting.


I'm not sure what you mean by this. What I'm trying to do is have the computer enter sleep mode (as its known on Windows, I think its formally known as S3 where the computer keeps providing power to the ram but everything else is off). The idea is that if no one accesses the computer for 10 minutes it goes to sleep. After that if it someone needs to use it they us wake-on-lan.

Is this possible?


Thanks.

---

