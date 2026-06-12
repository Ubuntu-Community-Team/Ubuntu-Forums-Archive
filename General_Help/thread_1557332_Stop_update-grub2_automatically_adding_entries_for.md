---
title: "Stop update-grub2 automatically adding entries for specific partitions(other distros)"
date: 2010-08-20
forum: General Help
---

### Post by interzoneuk on 2010-08-20
Hi.

I like to load other distro's via their own grub.

So at the min I add an entry to

/etc/grub.d/40_custom

i.e :-

> menuentry "Arch Linux X86_64" {
set root=(hd0,7)
chainloader +1
}

however when update-grub2 is run it also adds its own entries (for arch linux).

Is there a way to stop the update-grub2 script automatically adding a entry on a specific partition ?

Otherwise I get multiple grub entries .

Cheers

---

### Post by bcbc on 2010-08-20
> **interzoneuk said:**
> Hi.

I like to load other distro's via their own grub.

So at the min I add an entry to

/etc/grub.d/40_custom

i.e :-



however when update-grub2 is run it also adds its own entries (for arch linux).

Is there a way to stop the update-grub2 script automatically adding a entry on a specific partition ?

Otherwise I get multiple grub entries .

Cheers
sudo chmod -x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by interzoneuk on 2010-08-21
Thanks bcbc - that works !

Although that will disable it for all other partitions - Do you know of a way of just ignoring 1 specific partition/distro ?

i.e so that the script works as normal except it ignore anything on say /dev/sda7 ?

Cheers for your advise man !

---

### Post by bcbc on 2010-08-21
> **interzoneuk said:**
> Thanks bcbc - that works !

Although that will disable it for all other partitions - Do you know of a way of just ignoring 1 specific partition/distro ?

i.e so that the script works as normal except it ignore anything on say /dev/sda7 ?

Cheers for your advise man !

Yes - I thought you wanted to disable all of them :)

Drs305 has written an excellent tutorial on tweaking grub2, and one of them is about hiding a specific partition. [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

---

