---
title: "Thunderbird directory after upgrade"
date: 2010-05-02
forum: General Help
---

### Post by micha_silver on 2010-05-02
For years I have upgraded from distro to distro by keeping /home on a separate partition, then not formatting that partition during the upgrade, thus keeping all the personal stuff. Including the folder Thunderbird uses for mail and address books: ~/.mozilla-thunderbird. Then after starting Thunderbird in the new installation, I would just copy over all my mail from the old (randomly named) profile folder to the new one, and I'd have all my mail in the new installation/profile.

THis time, upgrading to Lucid, I checked after the installation that the Thunderbird folder was still there. Then I started up Thunderbird. As before it set up a new profile. Then I went to copy over the mail and address book files from the previous profile, and _nothing was there_. What I saw was that Ubuntu now saves the Thunderbird stuff under ~/.thunderbird, and the previous ~/.mozilla-thunderbird has become a soft link to the new folder. Apparently, at start-up, the softlink is force created ***wiping out*** all the old mail etc!

Has anyone else seen this? Does anyone know if this is by design?? If so, this is a gross mistake. Starting software should never blow away a user's files. Or am I missing something simple??
Thanks
-- 
Micha

---

