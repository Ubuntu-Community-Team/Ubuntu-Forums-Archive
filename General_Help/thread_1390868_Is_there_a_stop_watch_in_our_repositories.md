---
title: "Is there a stop watch in our repositories?"
date: 2010-01-26
forum: General Help
---

### Post by frenchn00b on 2010-01-26
Hello,

Something open source, and that could be also in command line (no X)
something like this [http://tools.arantius.com/stopwatch](http://tools.arantius.com/stopwatch)

Cheers

---

### Post by MarcDam on 2010-01-26
I've written a simple python script to do the job. Press enter to start the timer and stop the timer.

```
import time

while (True):
  raw_input("Press enter to start the timer...")
  startTime = time.time()
  raw_input("Press enter to stop the timer...")
  stopTime = time.time()
  print "Time: " + str(stopTime - startTime)

  again = raw_input("Restart timer (y/n)?")
  if again.lower() == "y":
    pass
  else:
    break

```

---

### Post by bluefrog on 2010-01-26
stopwatch

otherwise in command line
time command

example
time sudo aptitude update

---

### Post by Robster2 on 2010-01-26
> **frenchn00b said:**
> Hello,

Something open source, and that could be also in command line (no X)
something like this [http://tools.arantius.com/stopwatch](http://tools.arantius.com/stopwatch)

Cheers

I typed stopwatch into the synaptic package manager
>System>Administration>Synaptic Package Manager - I got a hit.

It looks very similar to what you had in the url.

It counts up and down.  Worth a look.

If can not find what you want from the repositories I would look at sourceforge.net

---

### Post by Robster2 on 2010-01-26
Sorry I missed the part about "no X"  the Python script looks pretty good.

---

