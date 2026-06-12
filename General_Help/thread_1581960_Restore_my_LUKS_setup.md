---
title: "Restore my LUKS setup"
date: 2010-09-25
forum: General Help
---

### Post by Blue-Tiger on 2010-09-25
Hi there!

Today I had to reinstall my system.  In their, I had 2 encrypted partitions (using cyrptsetup) plus an encrypted home-partition. It was no problem reimporting my home-partition, the installer did that for me.

Unfortunately, I didn't think about saving my old /etc/fstab and /etc/crypttab . So now I have trouble getting my old behaviour back for my 2 encrypted partitions (sda3 and sda8 ):

In the old system, it just "worked". Whenever I logged into the system, they would AUTOMATICALLY be mounted WITHOUT ASKING THE PASSPHRASE (the passphrase was the same as my user-pw anyways, I don't remember if that was by design (or even a necessity)  or not) and I think the system would unmount them when I logged out. (I think - since it is a single-user installation I never could really see if the partitions were mounted when I wasn't logged in).

Now I can still mount my partitions manually by doing

```

sudo cryptsetup luksOpen /dev/sda3 foo
sudo mount /dev/mapper/foo /foo

```

Also, I was able to find lots of instructions on how to get the system to mount the partitions at boot-time, and asking me for the passphrase in the process.

But I'd like to have the automated behaviour back that the old system had. However, I wasn't able to find any pointers, neither through googling nor by skimming through the manpages. Any help would be greatly appreciated! :)


EDIT: looks like what I was looking for is pam_mount . :)

---

