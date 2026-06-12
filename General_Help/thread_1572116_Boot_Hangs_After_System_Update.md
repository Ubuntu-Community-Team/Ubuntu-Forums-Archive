---
title: "Boot Hangs After System Update"
date: 2010-09-10
forum: General Help
---

### Post by crokett on 2010-09-10
I did a fresh install of Ubuntu 10.04 on a desktop.  I then did the system updates and on the reboot the system now hangs at the splash screen before the login screen.  I only get a blinking cursor on the text-based terminals.  I don't see the grub menu, I assume because Ubuntu is the only OS on this machine. So I can't boot to single user or text-only mode.  How can I figure out what is hanging it?

---

### Post by mohansathish on 2010-09-10
Hello crokett

If there is just a cursor blink and no other further improvement in loading ubuntu, try entering using a Live CD and do *sudo update-grub* .

If you can see the ubuntu loading, then press *Esc *and you can see where the booting hangs.

---

### Post by crokett on 2010-09-10
Well I figured out the shift key press displays the grub menu.  From there went to recovery mode.  I believe it is hanging at the fsck.  It checks /dev/sda1 which is my root partition and that passes.  I also attempted to create a RAID 0 array which -might- be the problem. So I will look at that.  for right now I can't even get it to boot to single-user mode.

Forgot to add, tried a live cd, the chroot command and then update-grub.  that failed.  the  system is at work and I am home now so will look at this again on Monday.

---

### Post by crokett on 2010-09-13
I fixed it.  It was the RAID array.  I had Fedora running on this system.  I installed Ubuntu then built the array again as a new one.  I thought it would just pick up the disks.  I guess not.

---

