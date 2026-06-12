---
title: "Ubuntu with two hard drives won't boot"
date: 2011-07-22
forum: General Help
---

### Post by just_jeepin on 2011-07-22
I have ubuntu 11.04 installed on a 80gb hard drive and everything was running fine. I then installed a second drive (1gb) for storage. It worked fine after a reboot but now it won't boot. I'm pretty sure it's just confused as to which drive is the boot drive. I'm not sure as to how to fix it in GRUB2.

Thanks for any help!

---

### Post by 2F4U on 2011-07-23
Do you get any error messages? How far does the boot process get? What about the boot order in BIOS, did you change that?

---

### Post by Mark Phelps on 2011-07-23
> **just_jeepin said:**
> I have ubuntu 11.04 installed on a 80gb hard drive and everything was running fine. I then installed a second drive (1gb) for storage. It worked fine after a reboot but now it won't boot. I'm pretty sure it's just confused as to which drive is the boot drive. I'm not sure as to how to fix it in GRUB2.

You don't "fix" it in GRUB -- you fix it in your BIOS drive boot order.

It looks like your BIOS may now be booting from the new drive.  Open your BIOS settings and change the drive boot order to have the old drive first.  That will "fix" it.

---

