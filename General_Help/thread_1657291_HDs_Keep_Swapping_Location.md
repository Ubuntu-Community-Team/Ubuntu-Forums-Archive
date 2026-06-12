---
title: "HDs Keep Swapping Location"
date: 2011-01-01
forum: General Help
---

### Post by codeblue2k on 2011-01-01
I have two HDs, one is a 80gb OS drive(Parallel ATA) and the other is a 1T storage drive (SATA). Well after each reboot they swap between /dev/sda and /dev/sdb, over and over again. One boot the OS is /dev/sda and the next its /dev/sdb, same goes for the second drive. This makes it difficult to setup fstab so it will mount the large storage drive on boot. Im not sure whats going on here or how to resolve it. Any help you can give would my much appreciated.

---

### Post by noah++ on 2011-01-01
Yeah, that happened to me too. It was annoying. I use LUKS with a boot password, so I had to reboot about half the time.

[Use UUIDs in **fstab**]("http://ubuntuforums.org/showthread.php?t=283131") instead of sd*x*.

---

### Post by mcduck on 2011-01-01
Just don't use the device names in fstab. Using label or UUID gives you a way to point to certain partition, regardless of what device name it has.

[http://linux.byexamples.com/archives/321/fstab-with-uuid/]("http://linux.byexamples.com/archives/321/fstab-with-uuid/")

---

### Post by codeblue2k on 2011-01-01
That worked like a charm. Thanks!!!

---

