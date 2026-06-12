---
title: "Booting from nForce FakeRAID: Have to hand correct grub.cfg after update-grub"
date: 2011-03-05
forum: General Help
---

### Post by krinchan on 2011-03-05
I was unaware of the difficulties of installing and booting Ubuntu from the "onboard raid" that the NVIDIA nForce chipsets provide.  However, I've managed to get it working reliably with one single caveat:

When update-grub builds the grub.cfg, it refers to all of my partitions as follows:

```
menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(**/dev/mapper/nvidia_caifaefg,msdos5**)'
	search --no-floppy --fs-uuid --set ed10cc43-426e-4206-b133-da9280752a48
	linux	/vmlinuz-2.6.35-27-generic root=UUID=edd50ae6-45ef-4168-9ab7-f18cc22683d4 ro   
	initrd	/initrd.img-2.6.35-27-generic
}

```

After mucking about trying to get the system to boot after my first kernel upgrade, I managed to discover that changing the device reference to the following would allow me to boot the system again.

```
/dev/mapper/nvidia_caifaefg5
```

The boot time error I receive when booting with the ",msdos" style mapper reference is:

```
Mar  1 19:44:54 SHIVA kernel: [   10.244722] device-mapper: ioctl: device doesn't appear to be in the dev hash table.
```

I am using an old non-GUID Partition Table.  This is because I was installing Windows 7 first and Ubuntu was having serious issues with how Windows was doing GPT.  Apparently the main GPT was not full sized and then the backup GPT was not at the end of the disk as expected.

So I'm guessing that the whole nvidia_blah,msdos5 is because of that.  However, it doesn't seem to explain why Grub would THINK that would work and it in fact does not work.  That's the biggest source of confusion on my part.

My questions are as follows:

First off, because as an IT person I want to know: 

Why does this sort of change work?  What does changing that device name change in GRUB's behavior?

Is there a setting in /etc/default/grub that would change the way it's naming these RAID devices?  Is there a value for this setting that would give me the device names that work, as explained above?

If there is no setting change I can make in /etc/default/grub, could I add a sed command on to the end of update-grub or can I make a modification to one of the scripts in /etc/grub.d?  What sort of change would be recommended?  How would I preserve this change through later package upgrades that would possibly rewrite these files?

Thanks ahead of time for any help.

-- David Kolb

---

### Post by krinchan on 2011-03-19
In case anyone arrives at the thread looking for help:

This change was not actually why Ubuntu booted successfully.  It was simply the fact that the first boot into a particular Ubuntu kernel since the last time the computer was powered down will always fail to mount the partitions.

I found that simply pressing "S" to skip mounting the partitions causes you to boot into an incomplete X environment.  I then Press Ctrl+Alt+F1 to get a terminal screen. I then either press Ctrl+Alt+Delete or login and run the command "sudo shutdown -r -v now".

Then, the warm boot into the kernel will work perfectly.

Note: If you log into another non-Linux operating system after powering up, your fist login to a Linux kernel will fail.

---

