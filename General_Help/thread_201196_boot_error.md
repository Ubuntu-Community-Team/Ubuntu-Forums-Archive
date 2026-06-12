---
title: "boot error"
date: 2006-06-21
forum: General Help
---

### Post by hard_i on 2006-06-21
After selecting ubuntu from grub and right after the splash appears, this happens:
```
/etc/init.d/rc: line209: /bin/sed: cannot execute binary file
```
and then it just hangs there.
? :roll:

---

### Post by Rui Pais on 2006-06-21
hi,
thats a strange error. 
That line makes the rc script goes through th rc*.d symlinks scripts and strip the names (ence the sed command) of the "SXX".

check if you got sed normally working and if there is some problem (like mounting)  your /etc/rc*.d/ directories.

Did this error appear suddenly? Is a fresh install? If no after what action did it starts to appear?

---

### Post by Daniel Ibrahim on 2006-06-21
I have had an update from Breezy 5.10 to Dapper from the Alternate CD
following the DapperUpgrades instruction from [https://help.ubuntu.com/community/DapperUpgrades](https://help.ubuntu.com/community/DapperUpgrades)

however after the second reboot, it didn't boot up to the GUI but got stuck short after the message that PCMCIA [[COLOR="Red"]failed[/COLOR]]

So I followed the instructions to move pcmcia and pcmciautils out of init.d
The problem didn't stop, the last thing I had was a screen with one blinking cursor on the top left end with no reaction to any key-combination except the Power-Reset or Power-OFF button on the box.

The last splitsecond before the almost blackscreen (as taken from my phone-camera) is attached as a jpg.

the last line reads:
```
Starting Hardware abstraction layer (hald)                              ok
```

Thanks for any suggestions

---

