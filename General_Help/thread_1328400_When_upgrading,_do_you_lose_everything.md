---
title: "When upgrading, do you lose everything?"
date: 2009-11-16
forum: General Help
---

### Post by BlackBullet on 2009-11-16
Hi, I'm new to Ubuntu, and I just noticed there's a new update out. So if I download tht update, and install it, do I lose my previous settings/files?

Thanks.

---

### Post by Giblet5 on 2009-11-16
You'll want to do a backup in case something goes wrong during the upgrade, but no, doing the upgrade keeps everything intact. It even installs the new versions of any extra packages you've installed.

Do a backup though...

---

### Post by holycow131415 on 2009-11-16
It is better to be safe than sorry.

---

### Post by arnab_das on 2009-11-16
i will make a confession here that i did manage to mess up my installation while doing the upgrade and had to lose all settings and files :(

had to do the fresh installation later.

backup your files and do a fresh installation. totally worth all the hassles!

---

### Post by Giblet5 on 2009-11-16
All of these testimonials are true to an extent.

I succeeded in upgrading six complex systems so far, and I've had no serious problems.

Do the backup though. That part isn't optional unless you really don't care if you lose everything.

---

### Post by undecim on 2009-11-16
> **arnab_das said:**
> backup your files and do a fresh installation. totally worth all the hassles!+1

A fresh install of 9.10 is definitely worth it. Not only is it easier (safer) than upgrading, the new ext4 filesystem is much faster than the ext3 that installs by default in 9.04

---

### Post by TetonsGulf on 2009-11-16
Agreed... I backed up all of my photos, music, docs and the like, then did a fresh install.

You SHOULDN'T lose everything on an upgrade, but I've found clean installs to be less troubling in the past and this time I could take advantage of the ext4 structure, a nice updated Firefox and the new software "storefront" I wanted to try out.

If you're worried about programs you've installed, at least those in the Ubuntu repos, try AptOnCD before you make the move and you will be able to get nearly all of them back. There may be some differences from Jaunty to Karmic in the repos, but you'll have all the program names and it's only a matter of searching for them to reinstall.

---

### Post by BlackBullet on 2009-11-16
Alright, Thanks everyone. I'll be sure to backup my stuff just incase :p

---

### Post by Iowan on 2009-11-16
I've upgraded this machine twice: Feisty>Gutsy>Hardy.  Lucky so far, no problems, but it becomes something of a hybrid system. Gutsy (and before) used */etc/network/interfaces* to configure networking - that got left in place when Hardy got installed. I'm not sure what else didn't get updated, but it's kinda nice to have my home directory intact (never built a separate partition).

BTW, it takes almost as long (or longer) to download the upgrade as it would to download the .iso.

---

### Post by id10twork on 2009-11-16
> **BlackBullet said:**
> Hi, I'm new to Ubuntu, and I just noticed there's a new update out. So if I download tht update, and install it, do I lose my previous settings/files?

Thanks.

You shouldn't, although you should back things up just in case. I did have one bad experience with an upgrade, and would have been lost if I hadn't backed up all my files.

---

### Post by ed-koala on 2009-11-16
Just to be safe, check what type of system you have ... I know things like RAID causes troubles in Karmic, so if you have that you'll want to know first.  Do a few searches on the forums first about any system things you may have like 64 bit or RAID might save you headaches later.

---

