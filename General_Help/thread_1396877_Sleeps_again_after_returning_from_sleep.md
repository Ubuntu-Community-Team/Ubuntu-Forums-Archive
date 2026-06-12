---
title: "Sleeps again after returning from sleep"
date: 2010-02-02
forum: General Help
---

### Post by voidux on 2010-02-02
Hello,

I configured Dell Latitude D620 to go to sleep mode (suspend to ram) when i close the lid. It suspends ok and then I open the lid. It wakes up ok, but few seconds after goes to sleep again! So I need to press the power button to force it to wake up.

Sleep button works just fine. /etc/acpi/sleep.sh from console too.

/etc/acpi/events/lidbtn
```
event=button[ /]lid
action=/etc/acpi/sleep.sh

```

update:
I noticed that it always goes to sleep again when I wake up laptop by opening the lid. For example if I run /etc/acpi/sleep.sh, pm-suspend or press the sleep button laptop goes to sleep, then i close the lid and when i open it back - the problem occurs.

---

### Post by ibuclaw on 2010-02-02
> **voidux said:**
> Hello,

I configured Dell Latitude D620 to go to sleep mode (suspend to ram) when i close the lid. It suspends ok and then I open the lid. It wakes up ok, but few seconds after goes to sleep again! So I need to press the power button to force it to wake up.

Sleep button works just fine. /etc/acpi/sleep.sh from console too.

/etc/acpi/events/lidbtn
```
event=button[ /]lid
action=/etc/acpi/sleep.sh

```

update:
I noticed that it always goes to sleep again when I wake up laptop by opening the lid. For example if I run /etc/acpi/sleep.sh, pm-suspend or press the sleep button laptop goes to sleep, then i close the lid and when i open it back - the problem occurs.

What is wrong with the default setup?
/etc/acpi/events/lidbtn
```

event=button[ /]lid
action=/etc/acpi/lid.sh

```

Regards
Iain

---

### Post by voidux on 2010-02-03
with the default setup it does not suspends on lid close. But if I suspend pushing the sleep button and close the lid after that it wakes up on lid open correctly though.

and with default setup something goes wrong. A few days ago I suddenly noticed that display stays turned off after lid opening. I didn't do anything to the system. But before that I was closing the lid, opening it and there was not nothing wrong, laptop just did nothing. But now it turns off the display and does not turn it back on.

update:
found some bug reports: [first]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/261084"), [second]("https://bugs.launchpad.net/ubuntu/+source/devicekit-power/+bug/425411"), [third]("https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/492649")
but i don't do anything to the power cord - it is plugged in always.

---

### Post by ibuclaw on 2010-02-03
Try this for kicks:

First, reset whatever changes you made back to their default values.
This means that the file and contents of:

/etc/acpi/events/lidbtn
```

event=button[ /]lid
action=/etc/acpi/lid.sh

```
**MUST** be as they are presented above.


Now we can do some local system setting up.

Create a 'local' directory.
```
sudo mkdir -p /etc/acpi/local
```
Then open a script file.
```
gedit lid.sh.post
```
And paste in the following contents:
```

#!/bin/sh

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    /etc/acpi/sleep.sh
fi

```
Then install it:
```
sudo install lid.sh.post /etc/acpi/local
```
Then close your laptop lid, and reopen to see what happens.

Regards
Iain

---

### Post by voidux on 2010-02-08
```

grep -q closed /proc/acpi/button/lid/*/state
if [ $? = 0 ]
then
    /etc/acpi/sleep.sh
fi

```Yeah, it works! Thank you!

---

