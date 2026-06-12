---
title: "Can't update/download GRUB2 -  mirrors.us.kernel.org down"
date: 2011-09-06
forum: General Help
---

### Post by thomsec on 2011-09-06
So I've borked my grub by moving and deleting partitions. I can follow the instructions to reinstall grub, but when I try to install grub, the connection to mirrors.us.kernel.org times out. Is there any other source for these files that I can point synaptic at?
Thanks

---

### Post by drs305 on 2011-09-06
You should be able to change to any of the other normal Ubuntu repositories to reinstall grub-pc (Grub2).

In Synaptic or Software Sources, change the repository (Settings, Repositories on the Ubuntu Software tab, 'Download from:').

---

### Post by thomsec on 2011-09-06
OMG! I got a response from drs305! I was using your guide to heal my machine. I'm going to mark this solved since I've fixed it by using your guide. I had set the mirrors as my default repository in synaptic, but I was installing grub by booting into the live cd and using the chroot method. Once into the terminal, I couldn't figure out how to download from any other repository. A nice Catch-22 situation - if I could boot normally I could reset the repository, but I couldn't boot normally without re-installing grub. I installed grub using chroot, but then got stuck in the grub> prompt. Once I got that configured correctly I could boot into my install and change repositories. I suppose I could have looked for instructions on editing the repositories list manually, but I didn't need to do that. This time anyway.
Great guide drs305. Thanks for the assistance.

---

### Post by drs305 on 2011-09-06
> **thomsec said:**
> Once I got that configured correctly I could boot into my install and change repositories. I suppose I could have looked for instructions on editing the repositories list manually, but I didn't need to do that. This time anyway.
Great guide drs305. Thanks for the assistance.

Glad you have it working again.

Just for reference, if you get the name of an alternate mirror (the one you cited wasn't working for me either), you could download the packages directly with a variation of this:

```
wget wget http://mirror.cs.umn.edu/ubuntu/pool/main/g/grub2/grub-pc_1.99~rc1-13ubuntu3_amd64.deb

```

The other way would be to edit the repository list. You could edit it manually or do it with the 'sed' command. The first section is the repository you want to replace, the second the one you want to use:

```
sed 's|mirrors.us.kernel.org|mirror.cs.umn.edu|g' -i /etc/apt/sources.list
sudo apt-get update

```

Hopefully you will never need to refer to this...  

Happy Ubuntu-ing !

---

