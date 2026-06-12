---
title: "Hibernate not working"
date: 2011-03-30
forum: General Help
---

### Post by cntrational on 2011-03-30
Trying to hibernate causes a blank screen to show up with a blinking text cursor. I have to force restart to get it working again.

---

### Post by cntrational on 2011-03-31
bump

---

### Post by r-senior on 2011-03-31
What machine are you using?

How much RAM does the machine have and how much swap space do you have configured?

```
$ free
```

For hibernate to work, you must have enough swap space to hold the contents of the RAM - because that's where it goes.

Can you suspend OK, rather than hibernate?

What version of Ubuntu are you running and which kernel are you updated to?

```

$ lsb_release -d
$ uname -rms

```

Sometimes support for hibernate/suspend appears as kernels are patched to support new devices. My laptop, for example, has never suspended properly with Ubuntu until installing 11.04 Natty with its 2.6.38 kernel.

---

