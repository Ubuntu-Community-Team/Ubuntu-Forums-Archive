---
title: "Lost all personal files"
date: 2011-11-17
forum: General Help
---

### Post by W29 on 2011-11-17
Hi

A few hours ago, I logged in into my account. All settings were reset, also all files in my home dir were gone.
So I logged out and logged back in. All folders that are not default home folders are back. Everything in folders like 'Documents', 'Pictures', 'Music',... are gone. Luckily I had a backup of everything. But seriously, I had no problems at all with version 10.04. In version 10.10 I had to install using nomodeset (because of the videodriver). Now with 11.10, I still have to install with nomodeset + there are occasional crashes during the boot. And now this...
I already installed Ubuntu 11.10 3 times because of this kind of problems :s. I'm really disappointed, so I'm gonna search for another distro.

My music files are still somewhere because my harddrive space is occupied (~100GB). Anyone who knows how I find them?
PS: My home dir is encrypted.

---

### Post by Matt Cadorette on 2011-11-17
I would probably use find or locate to see where they are, example:

(in terminal)

find / -name *.mp3 -type f

-or-

sudo updatedb
locate *.mp3

---

### Post by W29 on 2011-11-17
> **Matt Cadorette said:**
> I would probably use find or locate to see where they are, example:

(in terminal)

find / -name *.mp3 -type f

-or-

sudo updatedb
locate *.mp3

Haha. Sorry but that won't work. My music was in ~/Music. My home dir right now is ~30GiB.

---

### Post by W29 on 2011-11-17
The problem is solved. Some folders appeared twice in my home folder.
I couldn't see them in Nautilus, because they had the same folder name. But they were visible in my terminal.
How to deal with this:
Log out. Go to another screen (ctrl + alt + f1). (f1-f6 will do the trick)
Login as root (if you haven't set a root password, just log back in and type 'sudo passwd', log out again and go back to the other screen). Login as you own user (sudo su username).
Delete every folder that appears twice in your home dir (rm -rf folder). Make sure that you don't delete things twice! (rm -rf is irreversible)

Anyway. It is weird that something like this can happen.

---

