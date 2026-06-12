---
title: "eee pc lid issue"
date: 2010-11-30
forum: General Help
---

### Post by mulllhausen on 2010-11-30
hi. i know this issue has been covered in a lot of other threads, but i have read all these (at least over 5 of them!) and they all seem to have had a slightly different problem to me. so here is my problem:

im running ubuntu  9.10 karmic on my asus eee pc 701

im trying to get it to not shutdown when i close the lid and so far im having no luck. i've discovered that /etc/acpi/lid.sh is called when the lid is closed by adding the following lines at the very start of it:

```
date >> /tmp/x
echo "ran /etc/acpi/lid.sh" >> /tmp/x
```and closing the lid.

however if i then place the following after this:
```
exit 0
echo "should never get here" >> /tmp/x
```and thus prevent the actual functionality of lid.sh, the suspend-on-lid-close action still occurs!

this made me think that the acpi service is some kind of option and there is actually a higher level process which decides whether to use acpi or some other suspend service if acpi is not available. i tried
```
service acpid stop
```and sure enough the laptop still suspends on lid close!

any ideas as to how i can either
- solve my problem and prevent suspending when i close the lid, or
- determine which process is really suspending the laptop when i close the lid (coz it aint acpi!)

thanks in advance.

---

### Post by galvatron408 on 2010-12-01
has 9.10 to 10.10 changed the power management settings?

on my eee pc 1000 running 10.10, i just go to system->preferences->power management and change the value under "when laptop lid is closed" from suspend to blank screen.

---

### Post by mulllhausen on 2010-12-01
you're absolutely right galvatron408! its now under system -> power management -> on ac/battery power. just select "blank screen" for "when laptop lid is closed".

haha so simple i was looking in the wrong place.

---

