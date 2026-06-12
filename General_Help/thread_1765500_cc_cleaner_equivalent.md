---
title: "cc cleaner equivalent"
date: 2011-05-23
forum: General Help
---

### Post by qwertyjjj on 2011-05-23
Is there a cc cleaner equivalent for linux to clear out tmp, internet files, etc.?

---

### Post by satanselbow on 2011-05-23
There is computer janitor in the repos which can be installed through synaptic or from the terminal:

```
sudo apt-get install computer-janitor
```

or Ubuntu Tweak in a ppa 

```
**ppa:tualatrix/ppa**
```

:)

---

### Post by qwertyjjj on 2011-05-23
> **satanselbow said:**
> There is computer janitor in the repos which can be installed through synaptic or from the terminal:

```
sudo apt-get install computer-janitor
```

or Ubuntu Tweak in a ppa 

```
**ppa:tualatrix/ppa**
```

:)

I have computer janitor but I don;t think that's the same.
It only deletes a couple of programs.

---

### Post by matt_symes on 2011-05-23
Hi

Have a look at bleach bit.

```
sudo apt-get install bleachbit
```

Kind regards

---

### Post by flipper T on 2011-05-23
computer janitor is so dangerous that it is being dropped for 11.10

stick with ubuntu tweak

ps i know that it (computer janitor) can be used "safely", but i have broken my os each time that i have gone beyond the most basic settings

---

### Post by Matt__ on 2011-05-23
what's wrong with?
```
sudo apt-get clean && sudo apt-get autoremove
```

but ubuntu tweak is an easy gui option too.

---

### Post by oldos2er on 2011-05-23
> **qwertyjjj said:**
> Is there a cc cleaner equivalent for linux to clear out tmp, internet files, etc.?

/tmp is cleared on reboot. Not sure exactly what "internet files" are, can you elaborate?

---

### Post by qwertyjjj on 2011-05-23
> **oldos2er said:**
> /tmp is cleared on reboot. Not sure exactly what "internet files" are, can you elaborate?

temporary internet files / cache.
bleach bit seems to do the job.

---

### Post by galacticaboy on 2011-05-23
BleachBit is the best program out there!
'sudo apt-get install bleachbit'

Ubuntu Tweak is another great program.
[http://www.ubuntu-tweak.com](http://www.ubuntu-tweak.com)

Also the commands:
'sudo apt-get clean'
'sudo apt-get autoremove'

All of these are great and all work amazing for me!

---

### Post by oldos2er on 2011-05-23
If you're talking about a web browser disk cache, whichever browser you're using should have an option for this.

---

