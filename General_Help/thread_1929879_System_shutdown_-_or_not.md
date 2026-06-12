---
title: "System shutdown - or not"
date: 2012-02-22
forum: General Help
---

### Post by geekyhawkes on 2012-02-22
Hey;

so i dont understand why sometimes my machine will shutdown just fine with the menu and sometimes it wont. 

I try Sudo shutdown -P now and sometimes it works and sometimes not.
How can i find out whats going on and whats not working?  

Thanks

---

### Post by Ms. Daisy on 2012-02-23
On my ubuntu computer, sometimes the same thing happens when I'm logged in to more than one user account (ms.daisy and guest) at the same time. To resolve it I log off first then shut down successfully.

---

### Post by matt_symes on 2012-02-23
Hi

> **Ms. Daisy said:**
> On my ubuntu computer, sometimes the same thing happens when I'm logged in to more than one user account (ms.daisy and guest) at the same time. To resolve it I log off first then shut down successfully.

That is by design and can be changed by editing consolekit policies.

> **geekyhawkes said:**
> I try Sudo shutdown -P now and sometimes it works and sometimes not.
How can i find out whats going on and whats not working? 

Check the log files.

Kind regards

---

### Post by IWantFroyo on 2012-02-23
I just use
```
sudo shutdown -h now
```

See if you have more luck with that.

/Sorry, but I can't remember what the -P means.

---

### Post by matt_symes on 2012-02-23
Hi

> **IWantFroyo said:**
> /Sorry, but I can't remember what the -P means.

It means power off the computer.

If it's a typo then that a good call, IWantFroyo.

@OP. It's not Sudo but sudo. Linux is case sensitive !

Kind regards

---

### Post by geekyhawkes on 2012-02-24
hey sorry i should have got the case correct, im using sudo shutdown -P now

What log files can i look at to work out why the power down is not working?  

I only have one user account, I have the same problem if i use the xfce GUI shutdown option, but using sudo shutdown 'seems' to have more success...?

---

### Post by matt_symes on 2012-02-24
Hi

I would have a look in /var/log/syslog to start with.

It's strange that it is an intermittent problem.

Kind regards

---

### Post by geekyhawkes on 2012-03-01
Some answers, maybe i think its to do with my samba NAS and if it is mounted at shutdown or not. 

Im just doing a bit more digging first but the sys log hints at it (i would paste the code but x just crashed and now my sys log is refreshed! damn it!)

---

