---
title: "Can't boot up from XP hard drive!"
date: 2010-02-05
forum: General Help
---

### Post by demonic_crow on 2010-02-05
I have Window XP on my hard drive and now I can't get it to boot for some reason? I think it might have something to do with the MBR.  I removed the drive when I was trying to make a liveCD USB boot drive .  Do you think grub took it off or something.  Not sure if this is something I can fix in the terminal or not.  Thanks

---

### Post by labinnsw on 2010-02-12
[You could try Super Grub disc.]("http://www.supergrubdisk.org/")

---

### Post by lotharmat on 2010-02-12
Personally, I'd get an XP disk - Boot from that and go to 'repair' then type fixmbr.

This should correct the problem.

---

### Post by labinnsw on 2010-02-12
> **lotharmat said:**
> Personally, I'd get an XP disk - Boot from that and go to 'repair' then type fixmbr.

This should correct the problem.

That will fix MBR but destroy Grub.

---

### Post by john newbuntu on 2010-02-12
You can always fix grub once you know where your linux boot partition is.

---

### Post by ngrieb on 2010-02-12
You said "I removed the drive". What drive? Need more details.

---

### Post by demonic_crow on 2010-02-12
Ok first the only dis I have is a Sytem Restore so not sure if that will help me much.  What I did was I removed the hard drive from my laptop to make a Live Boot CD so I wouldn't mess it up.  I think I plug the hard drive into the laptop usb port to try and see if I could boot from it which didn't work.  So I placed it back into my laptop and tried to boot up and it wouldn't boot there either.

---

### Post by ngrieb on 2010-02-12
Ok, I'm still a bit confused by your swapping of disks. Let me see if I have this right:

1)   You had an internal HD you took out of your computer
2)   Then somehow created a boot CD with what I am supposing is your second HD...and then Installed.
       Ubuntu on this second drive, with the Windows disk still unplugged.

I'm not sure if this is what you did but:
If you did not have the Windows drive in at the time of the install, then that disk will not be found by grub, which I believe installs a small bit of code on the Windows drive for referencing.

In this case I think you can simply change your /boot/grub/menu.lst file to accommodate your addition of the Windows HD.

---

### Post by labinnsw on 2010-02-12
> **john newbuntu said:**
> You can always fix grub once you know where your linux boot partition is.

Which would not be necessary if you use Super Grub disc.

---

### Post by labinnsw on 2010-02-12
To: demonic_crow

> **ngrieb said:**
> In this case I think you can simply change your /boot/grub/menu.lst file to accommodate your addition of the Windows HD.

If you are unsure how to do this, Super Grub disc will do it for you.

---

