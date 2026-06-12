---
title: "what is firefox-bin?"
date: 2009-09-30
forum: General Help
---

### Post by kiridude on 2009-09-30
Hi, can someone please tell me what firefox-bin is? I looked around and wasn't able to come up with a satisfactory answer. Does anyone also know why firefox-bin eats so much cpu and ram?

I recently updated firefox externally because they made some important updates and Ubuntu is a bit slow to update. That is when I started seeing firefox-bin and its rather large appetite.

Thanks

---

### Post by scragar on 2009-09-30
firefox is a wrapper for firefox-bin that checks if firefox-bin is open and passes signals to and from it to prevent starting a new instance of firefox every time you click something that would open firefox(rss feeds, from your emails, maybe a html readme document or something).
Firefox doesn't normally have a large ram usage unless you are using flash or java, in which case it's not unusual for the ram usage to rise above 100MB(and if you keep doing things on it that number can rise to 300MB or more).

---

### Post by kiridude on 2009-09-30
Thanks scragar. Pretty cool name you got going on there ;)

---

### Post by dvo_photo on 2010-07-01
May I end the firefox-bin process? What will stop working if I do?


D

---

