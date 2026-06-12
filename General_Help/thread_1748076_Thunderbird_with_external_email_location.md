---
title: "Thunderbird with external email location"
date: 2011-05-03
forum: General Help
---

### Post by michellembrodeur on 2011-05-03
I have my thunderbird emails on my unraid server. works find in windows and ubuntu 9.04 did not work in 10's or now 11.04.

Problem I can not seem to make a permanent link to my server inside ubuntu any more.

i need to add this line int he profiles.
smb://neverwinter/michelle/Thunderbird/5fa789u0.Michelle
Which I have no problem going to using a file manager but not in thunderbird profile text file.

any help here.

I have both smb and samba installed.

thanks all

Oh!i have unity turned off since you cannot add anything to the desktop with it on. I like using the desktop

---

### Post by dcstar on 2011-05-04
> **michellembrodeur said:**
> I have my thunderbird emails on my unraid server. works find in windows and ubuntu 9.04 did not work in 10's or now 11.04.

Problem I can not seem to make a permanent link to my server inside ubuntu any more.

i need to add this line int he profiles.
smb://neverwinter/michelle/Thunderbird/5fa789u0.Michelle
Which I have no problem going to using a file manager but not in thunderbird profile text file.

any help here.

I have both smb and samba installed.

thanks all

Oh!i have unity turned off since you cannot add anything to the desktop with it on. I like using the desktop

Mount the external device in /etc/fstab.

---

