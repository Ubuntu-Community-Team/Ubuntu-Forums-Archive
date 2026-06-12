---
title: "'Install Updates' button on update manager doesn't work"
date: 2010-07-22
forum: General Help
---

### Post by ubnewbie2 on 2010-07-22
Update manager pops up telling me there are new updates, but clicking on the 'Install Updates' button does nothing.

However, if I click on Settings, then just close the settings dialog, it then says 'Starting Update Manager' and when that finished, the 'Install Updates' will work, but I have to do this every time I restart the computer.

---

### Post by svensandberg on 2010-07-22
I have the same problem, except clicking "Settings" does not help for me. I have to install the updates through Synaptic instead.
For me this started < 2 months ago in Karmic.

---

### Post by beav_35 on 2010-07-23
I have also noticed this on two different computers running Lucid.  I only noticed it starting in lucid though.  All I have to do is click "check" and it checks for updates then the install updates button works perfectly fine.

---

### Post by analog_G on 2010-07-23
> **beav_35 said:**
> I have also noticed this on two different computers running Lucid.  I only noticed it starting in lucid though.  All I have to do is click "check" and it checks for updates then the install updates button works perfectly fine.

I agree.  I see this issue almost every time the update manager runs.  It seems to be prevalent when I return to my computer after a while (overnight) and the update manager is awaiting my response.  Perhaps there is a timeout that disallows installation before checking for new updates?  I believe this is a bug.  anyone feel like submitting a bug report?

---

### Post by jmtd on 2010-07-23
> **analog_G said:**
> anyone feel like submitting a bug report?

[https://bugs.launchpad.net/update-manager/+bug/609148](https://bugs.launchpad.net/update-manager/+bug/609148)

---

### Post by analog_G on 2010-07-23
@jmtd
I read your bug report.  My situation (and others on this post) seems to be different.  Specifically clicking "Install Updates" does nothing, but if you first click "Check", then "Install Updates" it works as expected (no error messages).

---

### Post by NathanOsullivan on 2010-09-07
I've been encountering the same thing, so opened a bug [https://bugs.launchpad.net/update-manager/+bug/632728](https://bugs.launchpad.net/update-manager/+bug/632728)

---

### Post by totalz on 2010-10-19
I have tried the "solutions" above, but I can't get the manager to install the updates!!

Every time I click "Install Updates", it will just do "Reading Package Information" then nothing!!

The "sudo apt-get update" does not work for me as well, nothing after "Reading package lists... Done" :confused:

---

### Post by efflandt on 2010-10-19
I noticed the same thing as analog_G.  Not sure if it was because I had shutdown earlier with when Update Manager had come up minimized without doing updates then, or if it felt that the last check was stagnant.  But I noticed more updates on another computer.  "Install updates" button was unresponsive until I clicked "Check" (which added a bunch more), then Install Updates worked.

So maybe "Install Updates" is just unresponsive if you do not do updates in a timely manor after Update Manager started automatically.

---

### Post by miljenkom on 2010-11-17
I have also noticed this. For some reason pop-up window asking your password won't pop up. I also have same problem when trying to install new software with Ubuntu Software center. I found that when I start Update Manager with root privileges I have no problem any more.

---

### Post by Swagman on 2010-11-17
Have you changed prefs from LTS to Normal releases ?

---

### Post by spikehackerinc on 2012-04-09
> **miljenkom said:**
> I have also noticed this. For some reason pop-up window asking your password won't pop up. I also have same problem when trying to install new software with Ubuntu Software center. I found that when I start Update Manager with root privileges I have no problem any more.
Also starting having this problem about 2 days ago... I know this thread is old and what not... 

Opening update-manager with root fixed it for me... 

Peace Out :guitar:

---

### Post by oldos2er on 2012-04-09
Closed, necromancy.

---

