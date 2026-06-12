---
title: "Issue with DAC960 driver and newer Ubuntu releases"
date: 2010-03-13
forum: General Help
---

### Post by spiderwort on 2010-03-13
I have a desktop machine (specs below) which is successfully running Hardy (64-bit). I would like to upgrade. I always run a live CD before attempting an upgrade, because I've been bitten in the past with hardware not being properly supported in newer kernels.....

I can't get the CD/DVD to boot (lucid/karmic/jaunty). I have googled and RTFM, and in the process found kernel boot options "debug" and "initcall_debug". When using these, I get:

calling DAC960_init_module+0x0/0x60 [DAC960] @ 354

That last number varies on different boot attempts. That is the final message before the machine hangs.

I don't know where to take this at this point. Launchpad? Kernel developers? SCSI developers?

Machine specs:
Motherboard: TA790GX (uses AMD 790GX chipset)
CPU: AMD Athlon 3-core
Video: Radeon HD 3300 (on the motherboard) and NVidia GeForce 7300 (trying both to troubleshoot the issue.....)
CD: CD/DVD reader/writer, SATA
Hard drives: Mylex eXtremeRAID 2000 controlling 2 SCSI RAID5 drives
RAM: 4GB

Oh, and I have another machine in the house with a similar vintage Mylex controller on an older motherboard which installed and is running Karmic just fine!

Does anyone have any ideas on how to further troubleshoot this? Or who might be able to tell me what's not making it happy?

Thanks.

---

### Post by spiderwort on 2010-04-18
I've been poking and prodding at this issue in my spare time.

I have successfully booted (off CD/DVD): 
Zenwalk 6.0.1 (kernel 2.6.28 )
Arch 2009-08 (kernel 2.6.30)
Sabayon 5.2 (kernel 2.6.33)

And just to be clear, I can't boot (off CD/DVD):
Ubunty Jaunty (9.04) (kernel 2.6.28 )
Ubuntu Karmic (9.10) (kernel 2.6.31)
Ubuntu Lucid (beta1 10.04) (kernel 2.6.32)

As you can see I can successfully boot (oh yeah, and see the disk drives) several kernels in the same range that I can't get to run. The DAC960 driver has not changed.

I am left with the conclusion that Ubuntu has broken something that I need to boot.

Anybody have any ideas????

---

### Post by spiderwort on 2010-05-09
Fixed it.

I upgraded motherboard BIOS to the latest-and-greatest.

I am now happily running Karmic.

Who would have guessed the *motherboard* BIOS would have fixed it???!!

---

### Post by Weasel[DK] on 2010-05-17
Just had a similar problem on an older server at my friend.

We tried to install both th 8.04LTS-server and 10.04LTS-server, but they did freeze right after loading initrd.
A workaround was to disable the BIOS on the DAC960 controller. At the end of the installation grub failed to install, maybe beacause we disabled the BIOS :confused:,
 so we exited the installation without grub.
Then we rebooted and enabled the RAID BIOS and booted the installation cd in rescue mode and installed grub by hand.

Now the system runs just fine.

---

### Post by spiderwort on 2010-05-17
All those iterations I went through....I never thought to disable the card BIOS. Probably because you need it enabled to boot from the RAID array.

Don't worry, turning off the controller BIOS was not what made grub fail to install. I'm not certain I've _ever_ gotten grub to install from the installation with that brand controller. I did open up a bug in launchpad 2 - 3 years ago, but the only response I got was "it works for me...."

When I did this rebuild I created a second drive on the RAID array. Since this Mylex card talks to my motherboard BIOS well enough to let me choose the disk to boot from at boot time, I hope to spend some time troubleshooting what's up with the grub installation with Mylex/DAC960.

---

