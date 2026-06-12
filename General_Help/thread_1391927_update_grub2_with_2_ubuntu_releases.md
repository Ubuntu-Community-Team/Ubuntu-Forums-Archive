---
title: "update grub2 with 2 ubuntu releases"
date: 2010-01-27
forum: General Help
---

### Post by SanglierDesBois on 2010-01-27
Is there a way to have grub2 managing two installations from ubuntu on the same pc ?
I have two partitions, one with karmic, another with lucid. Grub is detecting automatically the two or more kernels, but assigning them to the same root partition !

Is there a way to make update-grub, detecting lucid kernel, and assigning it automatically to lucid partition, and the same for karmic ?

It seems, that os-prober, detects the lucid installation from karmic, and print the correct corresponding partition on the screen, but in the config file, the root partition is the wrong one, and os-prober doesn't detect karmic...

---

### Post by Leppie on 2010-01-27
if you're doing this from karmic, try using lucid's grub.
otherwise try doing it from karmic.

---

### Post by SanglierDesBois on 2010-01-27
it was the os-prober from karmic, that doesn't detect karmic...

---

### Post by Leppie on 2010-01-27
could you [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt?

---

### Post by SanglierDesBois on 2010-01-27
Here the output

---

### Post by Leppie on 2010-01-27
could you explain your partition table?

---

### Post by meierfra. on 2010-01-27
update-grub seems to get confused since  the kernels for lucid and karmic are both on your boot partition. (It does  not know which kernel belongs to which partition)  So you can either 

1)  Edit the Grub 2 configuration files so that update-grub  generates the correct grub.cfg

or

2)   Move the lucid kernel to the lucid partition and  delete the line for your boot partition in lucid's fstab.

I vote for 2), but either way is fine. So just lets us know what you prefer and we can give you detailed instruction, if needed.

---

### Post by SanglierDesBois on 2010-02-03
Previously with Grub1, I had on Boot partition for both testing and stable... so each system could update menu.lst when installing a new kernel on updates...

I find the idea to move the config file to /etc might be relevant according to the directory structure policy, but to have it in /boot, was much confortable...

I let Lucid install its kernel on its own partition, and it works, update-grub is correctly generating the grub.cfg file with the right kernel for the right partition...
But now, on lucid kernel update, I have to update-grub on karmic, or I have to maintain two /etc/grub config files... ?

Or is it possible to have a partition for what is in /boot/grub, so that each linux system would update is kernel into /boot, and use the same /boot/grub -> /dev/sda1 ??? or do grub also need files at the /boot root directory ?

---

### Post by meierfra. on 2010-02-03
> Or is it possible to have a partition for what is in /boot/grub, so that each linux system would update is kernel into /boot, and use the same /boot/grub -> /dev/sda1 ??? or do grub also need files at the /boot root directory ?

Yes, that should work. But  it could be a little but confusing since  your Grub menu  will look different depending on which "update-grub" was run last.

Instead of creating a separated grub partition, you could just bind one of the grub folders to the others (or make one of the /boot/grub's a symlink the other)

Disclaimer:  In theory this should works,  but I have not tested it and it might fail  due to bugs in Grub 2


Other options: Disable os-prober and use a "configfile" entry  or generic entry in 40_custom.

Let me know if you would like more details on any of the above.

---

