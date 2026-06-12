---
title: "hfs+ and group 99"
date: 2010-02-25
forum: General Help
---

### Post by gabrielcik on 2010-02-25
Hola!

I would like to be able to read and write on hd formatted as Hfs+ not journaled...

I know it is possible, but still I can't since ubuntu mount them with a different user: 99.

If I add my user to the group 99 will be fine? or exist another way to write on such file system?


A last question if use hfs+ not journaled it will be less safe for the files?

Thank you

---

### Post by kidders on 2010-02-26
Hi there,

I'm guessing you used MacOS to create the filesystem ... Group 99 is OSX's "_unknown" group, but that gid isn't normally used on Ubuntu. I'd suggest mounting the filesystem and chown-ing the mount point, to change the owner of your HFS+ filesystem's root to something sensible.

You'll only run into problems if you intend to share the filesystem with Macs ... In Linux, uids & gids assigned to human users tend to start at 1000, whereas they normally start at 501 on a Mac. As a result, the owner of any files you create on your HFS+ filesystem in one OS won't map to a known user on the other, and you'll find yourself constantly fighting with your computers for access to your own stuff.

If that applies to you, I suggest changing your MacOS uid & primary gid to the values used by Ubuntu (probably 1000, 1001, or something like that). That'll give you seamless file ownership on both operating systems.

> **gabrielcik said:**
> A last question if use hfs+ not journaled it will be less safe for the files?Yes, that's true. If you unmount the HFS+ filesystem uncleanly, you'll cause corruption that *might* normally have been handled by the journal. There are two ways of handling the extra risk ...[LIST]
[*]You could mount the filesystem with the "sync" option, to disallow asynchronous I/O. Doing this would adversely affect filesystem performance, but corruption would be less likely in the event of an unclean shutdown. NB: If the hard disk is an SSD, you _shouldn't_ do this, as it will significantly shorten its life.
[*]The alternative is just to be careful. Keep your filesystem unmounted when you're not using it, avoid installing experimental stuff that's likely to cause your Ubuntu to become unresponsive, and try to use good cables that won't fall out! The risk of data loss is about the same as with Ext2, so if you've used that in the past, you'll have a feel for how likely you are to run into trouble.
[/LIST]

Anyhow, I hope that helps.

---

### Post by gabrielcik on 2010-02-27
Thank you for the answer...

I use a macbook with leopard and a netbook with ubuntu... i simply wanted to share my external hd between these two computers, but as far as i see it looks not so safe :)

Any way if i change the ownership, should i change it to user or to root?
Is it not more simple to add myself to a group 99?

Thx!

P.s.
Can u say me which command to use for to make a simple scan disk? (i mean for ext4)

---

### Post by kidders on 2010-02-27
> **gabrielcik said:**
> i simply wanted to share my external hd between these two computers, but as far as i see it looks not so safeIt's *fairly* safe. For example, a lot of people routinely use FAT32 on external hard disks, which has no journaling either. Unjournalised HFS+ carries about the same risk of data loss.

> **gabrielcik said:**
> Any way if i change the ownership, should i change it to user or to root?That's up to you. If you're the only user of the disk, owning it yourself makes sense.

> **gabrielcik said:**
> Is it not more simple to add myself to a group 99?That's also up to you, really. There are several problems with doing that. For example ...[LIST]
[*]Group 99 is reserved for internal use by both OSX and Linux. For instance, if you were to install mail-related software onto your Ubuntu box (perhaps as a dependency of something completely different), it may want to use gid 99. Since you'd already be using it, the install process may fail.
[*]Files you create on OSX could be owned by a variety of groups (eg gid 20, "staff"), so relying on group memberships to access files is unlikely to make your life any easier. It's more usual to think in terms of the *user* ids.
[/LIST]That said, if you know what you're doing, you'll be able to side-step any problems arising from the use of reserved gids, and chgrp things as needed to grant yourself access to them.

> **gabrielcik said:**
> Can u say me which command to use for to make a simple scan disk? (i mean for ext4)You can use fsck for that, the same as on a Mac. NB: Just like OSX, you should _never_ use fsck on a mounted filesystem.

---

