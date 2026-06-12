---
title: "Firefox 3.0.12 available"
date: 2009-07-22
forum: General Help
---

### Post by CEB2nd on 2009-07-22
Firefox 3.0.12 showed up today in update manager.  I wonder what has
happened to version 3.5?  In windows, if you click "check for
updates" in the help menu version 3.0.12 now shows up
instead of 3.5.:confused:

---

### Post by michy99 on 2009-07-22
3.0.12 is the updated 3.0 which is the default for Jaunty. You can also install 3.5 alongside it. The package name is firefox-3.5. I believe 3.5 will be the default in Karmic.

---

### Post by GoldenSun on 2009-07-22
for jaunty
```
sudo aptitude install firefox-3.5
```

Then under the internet tab there should be a browser called something like "shireteka"...  you'll know it when you see it.  It is ff 3.5

---

### Post by dazzler on 2009-07-22
Just a heads up i applied this via update manager and it overwrote my firefox 3.5 install.

I wasnt paying much attention to the version numbers before updating.

---

### Post by michy99 on 2009-07-22
> **dazzler said:**
> Just a heads up i applied this via update manager and it overwrote my firefox 3.5 install.

I wasnt paying much attention to the version numbers before updating.

I doubt it overwrote your 3.5. Try starting it from the terminal.```
firefox-3.5
```

---

### Post by dazzler on 2009-07-22
> **michy99 said:**
> I doubt it overwrote your 3.5. Try starting it from the terminal.```
firefox-3.5
```

Tried that it starts firefox 3.0.1.2 :confused:

---

### Post by CEB2nd on 2009-07-22
FWIW, windows now shows version 3.5.1 available as an update.

---

### Post by dazzler on 2009-07-22
> **CEB2nd said:**
> FWIW, windows now shows version 3.5.1 available as an update.

Indeed cant understand why its not at least an 'option' in the repos of 'buntu seems to go against the freedom ethos of linux

---

### Post by Anonymous Rain on 2009-07-22
Why are there two versions of Firefox on Ubuntu, and why is the 3.5 version called Shiretoko? :confused:

---

### Post by mxboy15u on 2009-07-23
The last annoyance I had was the whole OpenOffice lack of upgrade for 8.10...now this firefox 3.5 failure. These are things which should be priorities to update...even in the middle of a distro.

---

### Post by Cheesemill on 2009-07-23
This isn't the way Ubuntu is designed to work.

Ubuntu only provide security updates to packages, not new versions of software (3.5 is a new version of Firefox, not an update to 3.0).

---

### Post by scouser73 on 2009-07-23
> **dazzler said:**
> Just a heads up i applied this via update manager and it overwrote my firefox 3.5 install.

I wasnt paying much attention to the version numbers before updating.

I had the update manager informing me of various updates one including Firefox 3.0.12, but I'm using Firefox 3.5.  Is there anyway to stop potention updates for previous versions of Firefox?

---

### Post by CEB2nd on 2009-07-23
Maybe we should start an email campaign to Mark Shuttleworth
about the way Ubuntu is being run.  It makes more sense to
me to stop the six month release cycle and instead use that
time to keep the LTS versions up to date and stable...but
that is just my opinion.:D

---

### Post by dazzler on 2009-07-24
> **scouser73 said:**
> I had the update manager informing me of various updates one including Firefox 3.0.12, but I'm using Firefox 3.5.  Is there anyway to stop potention updates for previous versions of Firefox?

Besides not applying that particular update not sure, i have reinstalled 3.5 and edited the menu to suit and all's well again, unless it bugs me to update again in a few days.

Although update manager is not showing it as an update atm.

---

### Post by irv on 2009-07-24
If you type
```
firefox-3.5
```
and you don't have it installed here you will see at the terminal.
[ATTACH]122280[/ATTACH]

---

### Post by irv on 2009-07-24
> **scouser73 said:**
> I had the update manager informing me of various updates one including Firefox 3.0.12, but I'm using Firefox 3.5.  Is there anyway to stop potention updates for previous versions of Firefox?

You can lock a version so it does not update.
[ATTACH]122281[/ATTACH]

---

