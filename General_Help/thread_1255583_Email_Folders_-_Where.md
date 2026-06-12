---
title: "Email Folders - Where?"
date: 2009-09-01
forum: General Help
---

### Post by RadarBat on 2009-09-01
I am planning to reinstall Ubuntu and I have a lot of saved email in folders in Thunderbird. Where are these in the Ubuntu menu structure so that I can save them to a CD disk? I have searched in the file system and not been able to find them.

---

### Post by StuartN on 2009-09-01
Mail is stored in ~/.mozilla-thunderbird/<PROFILE>/Mail where <PROFILE> is some unique alphanumeric string denoting your profile (there should only be one in a standard installation).

---

### Post by RadarBat on 2009-09-01
> **StuartN said:**
> Mail is stored in ~/.mozilla-thunderbird/<PROFILE>/Mail where <PROFILE> is some unique alphanumeric string denoting your profile (there should only be one in a standard installation).

The only thing that seems to be in "~/.mozilla-thunderbird/" is a file named "profile.ini"  I did not see any emails stored there.

---

### Post by StuartN on 2009-09-03
> **RadarBat said:**
> The only thing that seems to be in "~/.mozilla-thunderbird/" is a file named "profile.ini"  I did not see any emails stored there.

This is the default location, so check in Thunderbird under Edit->Account Settings. Look at the Local directory setting under the Server Settings for your mail account and at the Local directory setting under Local folders. One of the two will contain your mail.

---

