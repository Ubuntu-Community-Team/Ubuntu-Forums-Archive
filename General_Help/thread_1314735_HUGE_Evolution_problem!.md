---
title: "HUGE Evolution problem!"
date: 2009-11-04
forum: General Help
---

### Post by chaanakya_chiraag on 2009-11-04
Dear Ubuntuers,
   I have upgraded Ubuntu to 9.10 and am loving it except for one thing: Evolution.  Before upgrading, I was using Sunbird with Google Calendar.  I then used the Evolution Mirror extension to mirror my appointments to my "Personal" calendar in Evolution, and everything was handy-dandy.  Then, after I upgraded, I tried Sunbird again, but the whole Evolution Mirror thing had stopped working.  I think they did something to Evolution Data Server.  Anyway, I decided to add the Google Calendar to Evolution directly, but here is where I struck a pothole, so to speak.

   It doesn't work.  I get the following error whenever I try to authenticate the Google Calendar.  In other words, I can add it just fine, but when I go to actually refresh the calendar, it keeps asking me for my Gmail password.  Annoyed, I tried launching it in the Terminal, and my output was the following:

```
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Calendar'
e-data-server-ui-Message: Unable to find password(s) in keyring (Keyring reports: No matching results)
e-data-server-ui-Message: Key file does not have group 'Passwords-Calendar'

(evolution:8352): e-data-server-ui-WARNING **: Unable to find password(s) in keyring (Keyring reports: No matching results)

```

Does anyone know what this means and how this can be fixed?  Thanks in advance!

- Chiraag

---

### Post by stinger30au on 2009-11-04
out of interest when you upgraded, how did you do it?


did a little box come up on the screen and ask you to upgrade and u clicked yes and it downloaded a ton of stuff and took a few hours to update???

or did you backup your system, download a 9.10 .iso and reistall manually?

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)


the reason i ask is i have seen many installs fail and give wiered results after being upgraded when the user clicks the upgrade button and ubuntu goes merrily off on the net and downloads the data it wants

---

### Post by chaanakya_chiraag on 2009-11-04
Good question.
I kinda did both.  I have a separate /home partition, so I downloaded the 9.10 iso and installed it over the 9.04 root partition.  However, my /home partition, and therefore all of my settings, was left intact.  However, I did try completely resetting evolution by resetting all of the gconf evolution stuff and deleting all of the stuff in the .evolution folder.  Even then, it still doesn't work.

---

### Post by stinger30au on 2009-11-04
out of interest

what if you boot up using a 9.10 live cd and restore evolution from backup and setup sunbird??

does it work now???

---

### Post by chaanakya_chiraag on 2009-11-05
1) Sunbird still works, but I can't sync Sunbird events to Evolution using the extension (probably because the e-d-s stuff has changed).

2) Before starting this thread, I purposefully completely reset Evolution.  So completely that it showed the Evolution First Time Setup wizard when I opened it up.  I don't have any backups of evolution, so I can't try the live-cd thing.

---

### Post by chaanakya_chiraag on 2009-11-11
This issue was fixed in a recent update to Evolution.  Marking thread solved.

---

