---
title: "Borked USB Stick, Need Help"
date: 2011-01-17
forum: General Help
---

### Post by moore.bryan on 2011-01-17
So, for whatever reason it would seem I totally screwed-up my USB stick. I used UNetbootin to put a Linux Mint iso on the stick for a friend and then put-on a Fedora install without first clearing the stick. Then, forgetting I had stuff on the stick already, I dd'd it with another iso and received a "full" error. Now, I can't do anything with it... parted *seems* to allow me to format things and create new partitions and maps, but when I unplug the stick and then plug it back in, nothing. When I fire-up GParted, it won't even recognize the stick **and** when I try to clear it out via dd (i.e., "sudo dd if=/dev/zero of=/dev/sdb") I get the "full" error again.

Any ideas, oh faithful community?

Oh, and to add to our fun, GParted reports my 2GB stick is just a little over 400MB. :-)

SOLVED
My Debian 5.0 PPC iMac installed saved the day.

Now, I will just sit idly by and wait for an admin to delete/kill this thread. 

Goodbye, cruel world.

---

