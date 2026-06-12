---
title: "Google gadgets and Gnome desklets"
date: 2010-10-03
forum: General Help
---

### Post by DeMus on 2010-10-03
I installed Google gadgets and I think I will un-install it again. Every time I boot the order in which the gadgets appear is different. Some gadgets, like a calendar, appear with the wrong settings so I have to change it. Another one starts large so I have to read an advertisement which I don't want.
Is there a way to save what I have so I will have that again the next time I start?

I also installed the Gnome desklets but when I start it in terminal I get a list of invalid desklets:

```
jan@Desktop ~ $ gdesklets shell
jan@Desktop ~ $ _new_imp() takes at most 4 arguments (5 given)
URI in /usr/lib/gdesklets/Controls/URI is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
Time in /usr/lib/gdesklets/Controls/Time is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
EventPipe in /usr/lib/gdesklets/Controls/EventPipe is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
HDDTemp in /usr/lib/gdesklets/Controls/HDDTemp is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
Random in /usr/lib/gdesklets/Controls/Random is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
Sensors in /usr/lib/gdesklets/Controls/Sensors is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
Calendar in /usr/lib/gdesklets/Controls/Calendar is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
System in /usr/lib/gdesklets/Controls/System is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
ArrayBuffer in /usr/lib/gdesklets/Controls/ArrayBuffer is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
Popmail in /usr/lib/gdesklets/../../share/gdesklets/Controls/Popmail is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
Countdown2 in /usr/lib/gdesklets/../../share/gdesklets/Controls/Countdown2 is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
SideCandySytadin in /usr/lib/gdesklets/../../share/gdesklets/Controls/SideCandySytadin is NOT a valid plugin!
_new_imp() takes at most 4 arguments (5 given)
YahooWeather in /usr/lib/gdesklets/../../share/gdesklets/Controls/YahooWeather is NOT a valid plugin!
**
ERROR:/build/buildd/pyorbit-2.24.0/src/pyorbit-utils.c:39:_pyorbit_escape_name: assertion failed: (keyword_mod != NULL)
```
Nothing is visible at all.
I installed gdesklets and gdesklets-data. Does it mean this doesn't work at all or am I missing something?

---

### Post by DeMus on 2010-10-04
Nobody? Help please.

---

### Post by DeMus on 2010-10-05
Again: Help please. Isn't there anyone who knows why it is impossible for me to get the Gnome desklets working?
I gave up on the Google gadgets.

---

### Post by DeMus on 2010-10-07
Am I really the only one having problems with the Gnome desklets? Hard to imagine.

---

### Post by davidmohammed on 2010-10-07
[fix]("http://ubuntuforums.org/showthread.php?t=1524976") mentioned at the bottom of this thread.  hope this helps.

---

### Post by DeMus on 2010-10-07
> **davidmohammed said:**
> [fix]("http://ubuntuforums.org/showthread.php?t=1524976") mentioned at the bottom of this thread.  hope this helps.

Thank you for your answer. I did the one before last post in that thread and was told the program could not make contact with the daemon.
The last post in the thread is too high for me, I have no idea what to do and how to do it. So I just purged the complete package again and do without.
Thanks for trying to help me. Much appreciated, but it didn't work.

---

### Post by wilee-nilee on 2010-10-08
I use screenlets for a weather temp and conky for the rest.

Screenlets is in the repos and has a download link for other stuff.

---

### Post by DeMus on 2010-10-08
> **wilee-nilee said:**
> I use screenlets for a weather temp and conky for the rest.

Screenlets is in the repos and has a download link for other stuff.

Yes, and how does that help me? It's nice for you that you use screenlets for a weather temp and conky for the rest, but how do I benefit from that? For me it still doesn't work.

---

### Post by wilee-nilee on 2010-10-08
> **DeMus said:**
> Yes, **and how does that help me**? It's nice for you that you use screenlets for a weather temp and conky for the rest, but how do I benefit from that? For me it still doesn't work.

Thanks for a oh so positive response, I wonder why I even try at times.

---

