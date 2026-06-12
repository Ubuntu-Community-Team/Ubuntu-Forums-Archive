---
title: "Thunderbird 3.1.x with Google Desktop"
date: 2011-02-24
forum: General Help
---

### Post by terrywang on 2011-02-24
I got a new Dell Latitude E6410 to replace the old retired (still working great running Ubuntu x86, of course, replaced the original 80GB 5400RPM HDD with Seagate Momentus 7200.3 250G).

I installed Ubuntu 10.10 x86_64 on it and migrated the user settings and data over (tar /home /etc/, dpkg to export package list -> netcat -> e6410 -> untar, extract some config from etc.tar, manually install missing packages, 32->64-bit, don't dare to do dselect-upgrade).

All works great just like I am using a reborn D620. Today I found the problem which confused me:
Google Desktop 64-bit doesn't work with the Thunderbird 3.1.7 from repo.

I just don't see the 20k+ emails get indexed. Then I check add-ons and found the google desktop 1.2.0 add-on for Thunderbird is not compatible with 3.1.7.

Did some homework and managed to work around the compatibility check by adding extensions.checkCompatibility.3.1=false in about:config.

It appears to work, however, google desktop is still not indexing the IMAP mails and archived mails. They work great on 32-bit Ubuntu, I suspect it's related to 64-bit (google desktop, thunderbird or the add-don), but no clue yet.

In addition, I disable the Thunderbird 3 built-in Global Seach and Indexer (is it working great in terms of full text search?).

BTW: if there is good alternative to do the Thunderbird email full text index job, please share, I will be happy to give it a shot.

Any input will be appreciated.

Thanks,
Terry

---

### Post by terrywang on 2011-02-24
Anyone out there use Google Desktop to index Thunderbird emails on 64-bit Linux?

---

### Post by terrywang on 2011-03-02
Ok, finally I just figured out Google Desktop 1.2.0 doesn't work with Thunderbird 3.1.7+ on 64-bit Linux.

Even if extension compatibility check is disabled, google desktop extension seems to work with T-bird, the fact is that not all existing emails are to be indexed.

My observation is that only the accessed (opened) emails are indexed.

I gave up. Tried the built-in Global Search & Indexer (index stored in the sqlite database) appears to be pretty satisfactory so far. Along with the Quick Filter toolbar, it works even better than previous Google Desktop (22.3k emails with around 450MB index under ~/.google/desktop).

This is considered resolved:lolflag:

---

