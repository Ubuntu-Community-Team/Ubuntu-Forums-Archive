---
title: "Partition table destroyed in SATA hdd after connection via USB"
date: 2012-04-10
forum: General Help
---

### Post by franciscoruiz on 2012-04-10
Hi all,

I've replace my internal SATA disk (ubuntu + different partitions for the root, /opt and /home) with a new SSD. After installing ubuntu in the SSD I tried to access the data in the SATA one by connecting it to a USB with a regular drive case and the partition table had disappeared!!

I tried to recover it with *testdisk* but I only got like a million of completely useless files.

Any clue?

---

### Post by dcstar on 2012-04-11
> **franciscoruiz said:**
> Hi all,

I've replace my internal SATA disk (ubuntu + different partitions for the root, /opt and /home) with a new SSD. After installing ubuntu in the SSD I tried to access the data in the SATA one by connecting it to a USB with a regular drive case and the partition table had disappeared!!

I tried to recover it with *testdisk* but I only got like a million of completely useless files.

Any clue?

Plug it back into the motherboard, the USB hardware obviously addresses it differently.

---

### Post by Mark Phelps on 2012-04-11
Do you have your interal SATA ports set up as AHCI? IF so, when you then reconnected the drive through a USB channel, maybe it defaulted to IDE -- which could explain why the partition(s) could not be seen.

This is just a guess, though, as I have not actually tried this to confirm this problem.

---

### Post by franciscoruiz on 2012-04-11
> **dcstar said:**
> Plug it back into the motherboard, the USB hardware obviously addresses it differently.

I tried it but it was impossible to boot from it.

---

### Post by franciscoruiz on 2012-04-11
> **Mark Phelps said:**
> Do you have your interal SATA ports set up as AHCI? IF so, when you then reconnected the drive through a USB channel, maybe it defaulted to IDE -- which could explain why the partition(s) could not be seen.

This is just a guess, though, as I have not actually tried this to confirm this problem.

I have no idea, but if that were the case, would it be possible to recover the data?

Thanks!

---

### Post by Mark Phelps on 2012-04-11
> **franciscoruiz said:**
> I have no idea, but if that were the case, would it be possible to recover the data?

Thanks!

If, as I guessed, the USB interface defaulted to IDE, disabling you from seeing or mounting the partition, that should not have done any damage.

When you then reconnected the drive internally to your PC, it should have booted OK again.

You need to check in the BIOS to see that (1) the drive is detected and (2) if the SATA connection is IDE or AHCI.  If the SATA connection is NOW IDE, try changing it to AHCI to see if that works.

---

