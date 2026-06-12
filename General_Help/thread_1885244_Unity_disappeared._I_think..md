---
title: "Unity disappeared. I think."
date: 2011-11-22
forum: General Help
---

### Post by adredwood on 2011-11-22
Hi there all 

Relative newcomer to Ubuntu, tried it a few times but always had a stumbling block that kept me from completely adopting it. 11.10, however, I love - swift, efficient, and even my ipod works. That doesn't even happen in Windows much these days.

An interesting thing happened to me the other day, however. I was browsing a newly installed compizconfig, careful as always not to change anything I didn't understand, when the system hung entirely. I restarted, but all I got was a default background and the File / Edit / View menu on top left; no Unity popout, no clock etc in top right, nothing.

Finally figured I could log out and back in as guest, and also as me if I'm in 2D mode (as I am now), but any attempt to get back into 'normal' Ubuntu has the same effect.

Just tried something I read to restart Unity - logged in to normal Ubuntu, started terminal, restarted Unity with 

unity --replace

and got a long readout ending in '...this should never happen. You should probably file an error report'. All very mystifying, as I don't even know how to file an error report.

I realise my description of the runup to this is vague, but I don't believe I changed anything in compiz before it crashed out, so i don't know what I've done wrong...

Any help greatly appreciated -

Andy (:

---

### Post by LinuxFan999 on 2011-11-22
This is an extremely common issue, although I have actually seen a screenshot of it. Could you please post a screenshot if possible?

---

### Post by ubupirate on 2011-11-22
The command to reset Unity to default settings is:

```
unity --reset
```

Try that.

---

### Post by adredwood on 2011-11-22
Just tried unity --reset and no luck; it gave me a list of settings that were already set and then said process done or somethign similar. 

I'm afraid my Ubuntu skills dont extend to taking a screenshot, but will work it out if you think this is helpful. Any other ideas?

A (:

---

### Post by adredwood on 2011-11-22
Ok, I went back in to the system and tried to reinstall unity - seemed to work, the process completed, but it made no difference. Tried to reset again, same thing. I can't seem to screen grab, the only method I know is to open a program and I can't do that; also can't copy text as I can't open an editor to paste it into... sort of stuck, considering a repair / reinstall.

A (:

---

### Post by [Neurotic] on 2011-11-22
I've done this a few times. Short answer - I accidentally turned off the Unity plugin in compiz settings. Go into CCSM, and turn it back on.

---

### Post by adredwood on 2011-11-22
Hmmm, I thought resetting Unity would be enough to reactivate it. How do I get into compiz settings through the terminal?

---

### Post by [Neurotic] on 2011-11-22
ccsm

---

### Post by adredwood on 2011-11-22
Aha, that's done it. Thanks for the help guys!

---

