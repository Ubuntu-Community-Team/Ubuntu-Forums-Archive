---
title: "Struck at initramfs"
date: 2012-01-16
forum: General Help
---

### Post by manishm on 2012-01-16
Hi my system is not booting up.  I am struck with ext4_clear_journal_err. Looks like my OS partition is messed up and not allowing to boot the machine.

I followed another thread on similar issue reported by someone else here : [http://ubuntuforums.org/archive/index.php/t-1610145.html](http://ubuntuforums.org/archive/index.php/t-1610145.html)

I followed instructions given by rahul255 because system doesn't allow fsck too. But when I try to mount casper/filesystem.squashfs on to temp folder. I get following error

mounting /dev/loop0 on /tmp/fs failed: No such device. Despite the fact my disc is still in system.

another clues how can I restore system. Because I am even not able to re-install the machine.

---

### Post by dino99 on 2012-01-16
and booting with "recovery mode" fails too ?  (hold "shift" key down at bios end process to get the grub menu on single OS system)

booting with a livecd then running fsck on the faulty partition might fix the issue.

---

