---
title: "Google cal access using massive cpu"
date: 2012-05-20
forum: General Help
---

### Post by FredFrin on 2012-05-20
Hi

I just upgraded my Desktop to Ubuntu 12.04 LTS, all went very smoothly. I'm using gnome desktop.

After the upgrade my thunderbird mail client is at version 12.0.1.

I use this with Lightning & Google provider to access Google calendars. Worked fine in previous Ubuntu versions, but while it does actually work now, I see huge cpu usage when moving from one month to another in the calendar tab. I access 3 Google cals. Clicking the page fwd / bckwd buttons several time can lead to complete app crash.

Lightning 1.4
Google Provider 0.13.

Both installed via apt-get.

Anybody else experiencing similar probs?

cheers,
FF

---

### Post by FredFrin on 2012-05-20
had to be ...

Despite previous searching, shortly after posting I came across this:

[https://getsatisfaction.com/mozilla_messaging/topics/thunderbird_5_0_very_slow_and_using_huge_resources](https://getsatisfaction.com/mozilla_messaging/topics/thunderbird_5_0_very_slow_and_using_huge_resources)

The soln offered at the end (setting search filter from All Events to 'Events in this calendar month') provides a miraculous perf improvement.

Hope the info will be of user to some ...

---

