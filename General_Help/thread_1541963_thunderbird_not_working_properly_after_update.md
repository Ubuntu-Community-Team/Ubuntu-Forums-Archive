---
title: "thunderbird not working properly after update"
date: 2010-07-29
forum: General Help
---

### Post by buttersrocks on 2010-07-29
I ran my suggested ubuntu updates today and, after the update, thunderbird stopped working. For those of you who know thunderbird, the area under "folders" is completely empty, which leaves me completely unable to read my mail.

If anyone knows what might cause this or how to go back to the previous version of thunderbird (I don't know if it's still in the repos) I'd greatly appreciate it.

---

### Post by soldier1st on 2010-07-30
which version is it? atm 3.0.6 is the latest official version.

---

### Post by buttersrocks on 2010-07-30
yes, it is the latest version, 3.0.6

---

### Post by soldier1st on 2010-07-30
save your thunderbird profile and reinstall thunderbird. also what addons/themes do you have installed?it's possible one of them could be causing the issue.

---

### Post by buttersrocks on 2010-07-30
That was the first thing I did. It didn't help at all.

I use the default theme and have already disabled all of the addons.

---

### Post by soldier1st on 2010-07-31
what update did you install when this happened as if you can find the one that was installed then you could remove it, also in your synaptic repositories do you have prereleased and unsupported ticked? also save your profile for thunderbird and do a complete remove for thunderbird then do a reinstall.

---

### Post by buttersrocks on 2010-08-01
I updated from 3.0.4 (I think) to 3.0.6, but there were other updates that were done at the same time. I don't have an exact list of all of the updates. If anyone knows where I can find the older version of thunderbird, I could just install that, check if the problem still exists, and then determine if it's the new version of thunderbird or another update that's causing the issue. Thunderbird isn't displaying any errors when I attempt to debug.

---

### Post by buttersrocks on 2010-08-01
relevant information:

the message/start window does not display. also, the drop down box above the window with email/write new message/etc. in it does not show any items.

---

### Post by soldier1st on 2010-08-01
try this but backup your profile
[https://launchpad.net/~mozillateam/+archive/thunderbird-stable](https://launchpad.net/~mozillateam/+archive/thunderbird-stable) add that ppa then refresh but do not install anything then use ubuntu tweak and have it purge the ppa so it will revert the package to the system version which should solve your problem. also did you install nautilus elementary?

---

