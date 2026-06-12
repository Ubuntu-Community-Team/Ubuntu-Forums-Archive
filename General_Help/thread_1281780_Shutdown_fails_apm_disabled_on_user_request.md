---
title: "Shutdown fails: apm: disabled on user request"
date: 2009-10-03
forum: General Help
---

### Post by Jochus on 2009-10-03
Hi,

I'm currently unable to shutdown my Ubuntu system. This appears in the /var/log/messages file after firing "shutdown -h now"


```

Oct  3 21:55:39 passoa kernel: [101656.292171] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Oct  3 21:55:39 passoa kernel: [101656.292184] apm: disabled on user request.

```

Even when I push the power button, my system doesn't go down.

I didn't execute an "aptitude update". Nothing changed to the machine :-(

My version is Ubuntu 8.10

---

### Post by kayvortex on 2009-10-03
Wow, that's pretty unusual! What does the apm command spit out?
```
apm
```

(Edit: not that it's likely that you haven't just done a hard shutdown by now!)

---

### Post by Jochus on 2009-10-09
Sorry for the late post. This is it output:

```

jochus@passoa ~ $ sudo apm
No APM support in kernel

```

---

### Post by Jochus on 2009-10-09
Ok, now I installed the latest kernel. It shutsdown, but after the shutdown, the PC gets booted again :-/

```
jochus@passoa ~ $ uname -a
Linux passoa 2.6.27-11-generic #1 SMP Wed Apr 1 20:57:48 UTC 2009 i686 GNU/Linux
```

---

### Post by kayvortex on 2009-10-09
So, typing
```
sudo shutdown -h now
```
in a terminal causes the system to reboot?

What does:
```
type shutdown
```
print out?

Could you try entering:
```
sudo modprobe apm
```
and then try shutting your system down.

---

