---
title: "PPAs not updating"
date: 2010-03-11
forum: General Help
---

### Post by The Maxx on 2010-03-11
I recently re-installed Ubuntu Karmic on a new PC (about a month or so ago), and I just noticed that my PPAs are not updating when I run the update manager. I'm not a complete noob but I'm not all that hardcore or experienced. Is there something I am doing wrong?

When adding a PPA I open System>Administration> Software Sources and click on the "other software" tab. After clicking "add" I enter the APT line (*eg. ppa:banshee-team/paa)
and hit "add source". I hit close and let it reload and that's it.

This method worked fine for me before but now when I run Update Manager it never shows any updates for the PPAs I have added even though I know there is a newer version of the application available.

Am I doing something wrong or misunderstanding something? If so any help would be much appreciated.

---

### Post by mc4man on 2010-03-11
Assuming you've added the ppa(s) correctly (appears so) and that there are updated packages in them then try a simple
sudo apt-get update and see if any errors are produced ( or if it helps

Otherwise maybe try this ( normally is run weekly from cron

```
sudo update-apt-xapian-index
```

---

### Post by The Maxx on 2010-03-11
Hmmmm well, I ran sudo apt-get update, and that seems to have worked. I'm not sure why the update manager wasn't showing anything. Well thanks I guess I'll just try that if update manager fails me again in the future, I'm planning on doing a fresh install once Lucid comes out anyways so hopefully I wont run into any problems after that.

I'll post back here if I have any further problems.

Thanks again.

---

