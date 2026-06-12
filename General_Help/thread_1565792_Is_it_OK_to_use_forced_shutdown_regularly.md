---
title: "Is it OK to use forced shutdown regularly?"
date: 2010-09-01
forum: General Help
---

### Post by xtoph on 2010-09-01
Hello all,

Background you can skip:
I have an old Dell laptop, an Inspiron 2650, which I use primarily as an internet terminal at home.  I have switched back and forth between XP and different Ubuntu releases, and Lubuntu is what I am running with now.
At some point I upgraded and the hardware support for my laptop broke.  I have done multiple clean installs, and using any 10.04 Ubuntu distribution I have to disable ACPI in the Grub settings, or else my mouse and kb will not work.  So...

Question:
Since the OS shutdown feature can't turn off the laptop power with ACPI disabled, I often hit the laptop power button and skip the shutdown process entirely.  Most of the time I am only running Chrome, so I am not worried about losing or corrupting local data.  Is there any valid reason why this would be a problem?  Does the shutdown process do anything important enough to justify the hassle?

Thanks in advance,
xtoph

---

### Post by theDaveTheRave on 2010-09-01
xtoph,

are you saying you aren't even able to use the CLI to perform a shutdown??

eg
```

sudo shutdown -h now
```
or
```
sudo kill -1 -9
```

I'm not sure of the implications of not performing a 'clean' shutdown, but maybe you should consider more regular file system checks.

you can force them to be more regular in the the boot sequence, but I can't remember how to do it... I've had a quick search and nothing yet...??

David

---

### Post by xtoph on 2010-09-02
OK.  I can still shut Ubuntu down, the shutdown menu option still works for me.  But that only shuts down the OS and then I still have to hit the power button, so I don't usually bother.

---

### Post by theDaveTheRave on 2010-09-02
the machine should turn off when you do a
```
shutdown -h now  
```

are you saying that the power light stays on even thogh everything else is turned off?

The 'power light' remains on even on my laptop when the power cable is plugged in - although the light on the 'power button' is off.

My wife has a new laptop and the 2 are the same thing, but the colour becomes more intense when the button is pressed.

Don't know if that info helps?

David

---

### Post by wojox on 2010-09-02
Take a look at this as well [DebuggingACPI]("https://wiki.ubuntu.com/DebuggingACPI")

---

### Post by paul079 on 2010-09-03
try using sudo shutdown -P now; -h will halt the system, not necessarily power it off

i always shut mine down from the command line anyway

---

### Post by Strongman332 on 2010-09-03
or try

```
sudo poweroff
```

---

### Post by RedTech2010 on 2010-09-03
I think it can affect to your OS that may cause into file corruption.

---

