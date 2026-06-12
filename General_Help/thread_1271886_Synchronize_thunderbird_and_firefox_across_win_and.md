---
title: "Synchronize thunderbird and firefox across win and linux"
date: 2009-09-21
forum: General Help
---

### Post by David_jcd on 2009-09-21
Hi!
I'm going to install ubuntu  on my laptop, so i'll have 3 partitions: win, linux and a fat32 partition for documents and shared folders.
Does anybody know how to synchronize firefox and thunderbird profiles across win adn linux, so that any change in window's firefox (or thunderbird) will be automatically applied in linux's (for example, the downloaded mails, the bookmarks or the passwords)?
I found a couple of guides, but i think i have to create a new profile to make it work, and i'd like to use the profiles i already have.

Sorry for my english...

---

### Post by Mr_JMM on 2009-09-21
Firefox: Install an add-on called xmarks. It syncs your bookmarks and passwords but if the settings will still be different.

Thunderbird: Use IMAP if possible or better still, gmail and do away with thunderbid altogether.

Alternatively, but note I haven't tested this across OS's, you could move the profiles file for both firefox and thunderbird to the shared fat32 partition then change the settings to use this file rather than the default profile.

And honestly, you don't need to apologise for your English.

---

### Post by oldfred on 2009-09-21
I do exactly this. I copied the entire profile to the FAT32 partition and redirected my windows copy to that location. I installed firefox and thunderbird and let it create default profiles. I then changed the profile ini file to find the FAT32 version. You also will need to have a permanent mount point for the FAT32 partition set up in fstab so linux can always see the profiles. I have also updated from version 2 to 3 to 3.5 in both windows & Ubuntu without any issues.

I created /share as a mount point and this is my profile.ini in 
/home/fred/.mozilla-thunderbird

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/fred/share/mozilla/thunderbird/profiles/lyu25irb.default
Default=1

```

More info:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

### Post by David_jcd on 2009-09-21
> **Mr_JMM said:**
> Firefox: Install an add-on called xmarks. It syncs your bookmarks and passwords but if the settings will still be different.

Thunderbird: Use IMAP if possible or better still, gmail and do away with thunderbid altogether.

Alternatively, but note I haven't tested this across OS's, you could move the profiles file for both firefox and thunderbird to the shared fat32 partition then change the settings to use this file rather than the default profile.

And honestly, you don't need to apologise for your English.thanks a lot!
> **oldfred said:**
> I do exactly this. I copied the entire profile to the FAT32 partition and redirected my windows copy to that location. I installed firefox and thunderbird and let it create default profiles. I then changed the profile ini file to find the FAT32 version. You also will need to have a permanent mount point for the FAT32 partition set up in fstab so linux can always see the profiles. I have also updated from version 2 to 3 to 3.5 in both windows & Ubuntu without any issues.

I created /share as a mount point and this is my profile.ini in 
/home/fred/.mozilla-thunderbird

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/home/fred/share/mozilla/thunderbird/profiles/lyu25irb.default
Default=1

```

More info:
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

thank you, too!
I will try, and, eventually, ask more questions if I'll need to!

---

