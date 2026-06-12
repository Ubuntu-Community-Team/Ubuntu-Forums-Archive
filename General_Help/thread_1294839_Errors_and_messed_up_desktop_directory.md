---
title: "Errors and messed up desktop directory"
date: 2009-10-18
forum: General Help
---

### Post by kornfan16099 on 2009-10-18
[FONT=Arial][SIZE=2]Hey guys, I've been using Ubuntu for a few months now and compared to windows vista[/SIZE] (Which prompted me to change to ubuntu by putting itself into an infinite loop after an official windows update messed it up).
[SIZE=2]However when i was first using ubuntu [SIZE=1](Jaunty)[/SIZE] i seem to have messed something up which means that whenever i install anything i recieve an error code which says something similar to the following[/SIZE] [SIZE=1](now using Karmic)[/SIZE]
[/FONT]> W: Duplicate sources.list entry [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic/universe Translation-en_GB (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic_universe_i18n_Translation-en%5fGB)
W: Duplicate sources.list entry [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic-updates/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_karmic-updates_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com]("http://security.ubuntu.com/") karmic-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_karmic-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems[FONT=Arial][SIZE=1]
[/SIZE]
[SIZE=2]Although it states there is an error the updates and installations usually work fine but it's a bit of an annoyance and sometimes messes up installations.

Also for some reason my desktop shows files in my user file "/home/jake" Rather than in my desktop folder "/home/jake/Desktop" and this has created the cluttered desktop i have today.
If anyone could offer any solutions then i would be really greatful.[/SIZE]
[SIZE=3]Thanks
[SIZE=4]Jake .R. Baker[/SIZE][/SIZE]
[/FONT]

---

### Post by P4man on 2009-10-19
Hi

The problem with the repo's is  easily fixed. Go to system > administration > software sources and find the duplicate entries in the "other software" tab (they are probably already included because of whats checked in "ubuntu software"). Just uncheck or remove them there.

As for the desktop, try starting gconf-editor. Then browse to apps > nautilus > preferences. Make sure "desktop_is_home_dir" is unchecked.

---

