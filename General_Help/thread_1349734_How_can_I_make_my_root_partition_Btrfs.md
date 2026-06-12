---
title: "How can I make my root partition Btrfs?"
date: 2009-12-08
forum: General Help
---

### Post by lightningfox on 2009-12-08
Hello

I am using Ubuntu 9.10.

I want to make my root partition btrfs.

But there is no Btrfs option in the Ubuntu Livecd installer.


How can I make my root partition Btrfs?

---

### Post by renkinjutsu on 2009-12-08
Don't do it. It's not stable, and it would be a horrible idea to try to boot from it.. i'm not even sure if Grub2 supports it.

---

### Post by toobuntu on 2009-12-10
Per the [blueprint]("https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-btrfs-support"), btrfs support should land in alpha 3.

Per the [spec]("https://wiki.ubuntu.com/FoundationsTeam/BtrfsSupport"), installer support is currently targeted for lucid+1:
> If we manage to work fast enough to add installer support for Lucid, it will not be presented by default, as it is not clear that the filesystem is stable enough yet ... btrfs supports smooth **upgrades from ext3 and ext4** (and also reverting back!), so that **will be the installation path for adventurous users**. (emphasis added)

---

