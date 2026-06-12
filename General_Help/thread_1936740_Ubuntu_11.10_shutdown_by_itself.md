---
title: "Ubuntu 11.10 shutdown by itself"
date: 2012-03-06
forum: General Help
---

### Post by Th3Alchemist on 2012-03-06
Hi!

Im having an issue with my Ubuntu 11.10: It shuts down by itself while im using it with no kind of warning. It just happend again any reason why? Happend already 3 times

I'm kindly new at ubuntu. If I need to post a log here, please tell me how.

Thank you!

---

### Post by Frogs Hair on 2012-03-06
If it is powering off completely the cpu or some other hardware may be over heating . If it is crashing you would be returned to the login screen .

You can post log or terminal output by using the # symbol on the reply box tools . Just copy and paste the contents . Look in the log file viewer for any thing that may give a clue as to what may be happening .

---

### Post by MG&amp;TL on 2012-03-06
> **Th3Alchemist said:**
> Hi!

Im having an issue with my Ubuntu 11.10: It shuts down by itself while im using it with no kind of warning. It just happend again any reason why? Happend already 3 times

I'm kindly new at ubuntu. If I need to post a log here, please tell me how.

Thank you!

Are you on a laptop or a desktop? If on a desktop, we can mostly remove the overheating/battery life causes.

---

### Post by Th3Alchemist on 2012-03-06
It is a laptop, but I never had issue with overheating before and also batter was full with power source plugged...

I will post the log as soon as I boot ubuntu again

By the way, how can I view the system logs?

---

### Post by Th3Alchemist on 2012-03-06
All right, guess you were right! (overheating)

```
Mar  6 18:58:21 Marc-R510 kernel: [16599.350743] Critical temperature reached (105 C), shutting down.
```

---

### Post by winh8r on 2012-03-06
Now that you know the cause of the shutdown:

Make sure all the vents around the laptop are clean and free from dust etc.

Even though you were running on the power supply, the battery might still be failing, do some checks on the capacity of the battery and replace if necessary.

Also if you are not using a particular application , close it rather than leaving it running in the background.

Disabling desktop effects or using a lighter desktop environment may also help if the problems continue.

Hope this helps

---

