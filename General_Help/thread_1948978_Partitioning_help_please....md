---
title: "Partitioning help please..."
date: 2012-03-29
forum: General Help
---

### Post by varunpr97 on 2012-03-29
I am not new to Linux(in fact am a Linux user for 5 yrs). But the one place I screw up is the partitioning. I want to install arch with Ubuntu in dual boot.  I want to make 2 primary partitions with mount point as / for arch and Ubuntu and 1 4gb partition for swap(to be shared by both arch and Ubuntu). I want to install arch first and then ubuntu so as to get grub 2. Will that work or do I need separate partitions for /boot,/var n /home? I usually let d automatic partitioner do its job so this time I am really screwed up. Any help will be appritiated. Also is the swap files shared by default or do I have to change something n hibernate won't work if I change distros will it? I apologise for my poor english as it is my 3rd language.

---

### Post by oldfred on 2012-03-29
I have not installed Arch, but I think it still uses grub legacy (?). If so install its grub to the / partition (PBR) not the MBR. Then from Ubuntu you could also chainload to the grub in the partition if you want or let os-prober find all the installs and boot. But os-prober has to be re-run on every update of Arch to find the new kernels where chainloading will see the updated grub legacy menu.

You may want to keep system partition smaller and have a shared data partition. Not sure what UID or GID's Arch uses as a default, as Ubuntu users 1000. If not the same data sharing can be a bit more difficult.

Again I do not know Arch, but with Ubuntu you do not need separate partitions:
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I do prefer to have /home or a data partition separate, but:

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by varunpr97 on 2012-03-30
> **oldfred said:**
> I have not installed Arch, but I think it still uses grub legacy (?). If so install its grub to the / partition (PBR) not the MBR. Then from Ubuntu you could also chainload to the grub in the partition if you want or let os-prober find all the installs and boot. But os-prober has to be re-run on every update of Arch to find the new kernels where chainloading will see the updated grub legacy menu.

You may want to keep system partition smaller and have a shared data partition. Not sure what UID or GID's Arch uses as a default, as Ubuntu users 1000. If not the same data sharing can be a bit more difficult.

Again I do not know Arch, but with Ubuntu you do not need separate partitions:
Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

I do prefer to have /home or a data partition separate, but:

Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/?t=1675381](http://ubuntuforums.org/?t=1675381)

thanks a lot...ya, arch uses grub legacy. So can I not install d grub bootloader in arch n then install it with Ubuntu so that it  will recognise both the operating systems? once again thanks a lot.

---

### Post by oldfred on 2012-03-30
If you install grub legacy to the MBR and then install Ubuntu it will overwrite the MBR and grub2's os-prober should find your Arch install and let you boot it.
Some systems it does not find as well as others and that was why is suggest the option of chain loading.

I do not think grub legacy saved the reinstall location. But grub2 does and on a major grub update, it will auto reinstall to the place it was installed originally. So with multiple systems, an update may all of a sudden change which system you boot from.

---

### Post by varunpr97 on 2012-03-31
> **oldfred said:**
> If you install grub legacy to the MBR and then install Ubuntu it will overwrite the MBR and grub2's os-prober should find your Arch install and let you boot it.
Some systems it does not find as well as others and that was why is suggest the option of chain loading.

I do not think grub legacy saved the reinstall location. But grub2 does and on a major grub update, it will auto reinstall to the place it was installed originally. So with multiple systems, an update may all of a sudden change which system you boot from.

Thanks a lot!

---

### Post by 1clue on 2012-03-31
This isn't exactly what you're talking about, but it's related.

I would recommend using lvm2 instead of old-school partitions.

What this gets you is the ability to rework your partitions after installation.  You can have multiple distros (not Windows) on these same volume groups, and you can add or remove drives from the volume group, move partitions around, resize, whatever without actually shutting the system down.

The only real caveat here is that any partition that needs the ability to be resized needs to be ext3 or better, or some other type that supports resizing, preferably on the fly.  I have ext3, ext4 with XFS for large files.

What that means is you can start with minimal partition size without trying to anticipate final size.  I get warnings all the time during updates or installs, then quickly resize the partition in question while the install is going on, or retry the install afterward if I'm not fast enough.

Your partitions wind up being the size they need to be, rather than the size you thought plus some sort of hypothetical safety factor.

---

