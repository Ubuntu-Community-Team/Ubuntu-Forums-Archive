---
title: "new file structure in 11, subpartitions (?), btrfs"
date: 2011-08-27
forum: General Help
---

### Post by hungrybeast on 2011-08-27
So, I just installed 11.04 and I've run into some questions. This came about when I edited my fstab to get a partition mounted to a static address, and figured while I was at it I'd make it look more normal and use device names instead of uuid.

I took one look at the new thing about home being a "subpartition" designated with (I think, overwrote it like an ***..) sub@****** in the option column, and I decided that was retarded and just replaced the whole thing with a normal / partition mounting scheme. Of course, this then broke my login..which yielded an error regarding iceauthority, so I first figured the installer must have encrypted my home partition in error. But, having inspected it from livecd, I now see that the root of the OS partition is actually structured as two folders: '@' and '@home'. So, I want to know what that's about: why?, can I just copy stuff around to be normal if I so choose?, and if not, how should my fstab look to support this scheme?..now that I overwrote the default one.

Additionally, I kind of chose btrfs for my / without much thought, figuring that, being reiser4-like, it was a natural choice for my new SSD. I noticed, while in synaptic looking for the tuning utility, that there's a disclaimer to the effect that it's actually experimental/unsupported. So I was wondering if there was significant enough risk of failure related to this that I should go with reiser3 instead.

---

### Post by searchfgold6789 on 2011-08-27
I have no idea what you are talking about. :KS
That said, I'll try to explain that post to myself. Your home directory is "/home/{your username}/", which is synonymous with ~. It is not a separate or "sub" partition, although you can mount another partition on it instead of it being part of your / partition. It should not be in your fstab unless you do not want your home directory to be on the same partition or device as your root (/) partition.
"<username>@<computername>$" is simply a prompt.
And, I know of no real reason why one should choose a root filesystem to be anything except ext4. Do let us know why you chose reiserfs or btrfs over the default ext4.
If I did not answer your questions thoroughly, do post back!
 - search

---

### Post by hungrybeast on 2011-08-27
I know it must appear insane/novice that I think root directory looks like this division, because inside the install it hides it from you. You have to view it with something else like a livecd, I believe. @home contains just my user account's home folder, while @ contains a normal /, having an empty /home folder. This is a regular install with one large / partition and no encryption. I had never seen an fstab like that one before in 5 years of linux usage.

I guess I like this btree stuff because it seems fancy and I'm the sort of person who wears shoes with 12 colors. Also, Hans Reiser is a badass.

---

### Post by redmk2 on 2011-08-28
> **hungrybeast said:**
> I know it must appear insane/novice that I think root directory looks like this division, because inside the install it hides it from you. You have to view it with something else like a livecd, I believe. @home contains just my user account's home folder, while @ contains a normal /, having an empty /home folder. This is a regular install with one large / partition and no encryption. I had never seen an fstab like that one before in 5 years of linux usage.

I guess I like this btree stuff because it seems fancy and I'm the sort of person who wears shoes with 12 colors. Also, Hans Reiser is a badass.

Before you use btrfs you should read up on it.  It works more like *ZFS pools* than the basic Linux ext file system.

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=1389279") for the Ubuntu discussion on root installation and [**_[COLOR="Blue"]here[/COLOR]_**]("https://help.ubuntu.com/community/btrfs") for the Ubnuntu Community btrfs page  You can  see  a complete tutorial for a btrfs install on the btrfs.kernel.org wiki [**_[COLOR="Blue"]here[/COLOR]_**]("https://btrfs.wiki.kernel.org/index.php/Getting_started").

When I upgrade I think I would try to install the OS on ext4 and use btrfs for data only (instead of an LVM setup).

---

### Post by hungrybeast on 2011-08-28
So does that mean each '@' folder represents a btrfs vdev?

---

