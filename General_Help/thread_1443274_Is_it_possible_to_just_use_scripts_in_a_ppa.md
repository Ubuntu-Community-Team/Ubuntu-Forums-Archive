---
title: "Is it possible to just use scripts in a ppa?"
date: 2010-03-30
forum: General Help
---

### Post by narnie on 2010-03-30
Hello,

I have made a script to automatically update opendns with the current router external IP.

I have built this into a deb package that can be distributed in the normal way for debs.

What I would like to do is take it up a notch and make a ppa on launchpad.net. This way when I make changes, the next time my sister 5 hours away will get the update without me having to get her a deb and manually do it, but it just happens with regular system updates.

When reading about his, I see that we can't just simply upload debs. Seems like launchpad wants to just build binaries (which is not necessary in this case). I just need to make my script to be packaged into a deb by the PPA.

Is that not possible? The script is simple wget utilization and adding a line to /etc/crontab. Nothing really complex, but quite useful.

Any help would be greatly appreciated.

Yours,
Narnie

---

