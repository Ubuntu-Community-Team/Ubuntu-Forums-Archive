---
title: "2 Boot screens"
date: 2009-07-01
forum: General Help
---

### Post by linuxguy5 on 2009-07-01
Hello,
I just got an HP Mini 110 [Netbook] with XP pre-installed. I downloaded the most recent version of wubi and Ubuntu. (I've used them both before). When I start the computer, I am first presented with the HP icon, as expected. Then, I am presented with a bootloader that looks like the one on the Wubi website. If I move down to Ubuntu, it tells me my XP OS is corrupted, and to repair. But If I select XP, I am presented with a screen giving me 2 options like the first screen, only this time, I can boot from XP and Ubuntu.

Any ideas on how to remove the first screen? The first screen looks like the bootloader I see on Vista, while the second screen is normal (And what I want).
Thanks.

---

### Post by Geoff918 on 2009-07-01
Hmm, sounds like you did more than one install? One with GRUB (full Ubuntu install) and one with Wubi (Windows Bootloader)?

---

### Post by linuxguy5 on 2009-07-01
Hi,
Nope. It came with XP installed, and all I did was use Wubi. 
Thanks.

---

### Post by linuxguy5 on 2009-07-02
Hi,
The first boot screen looks like the on here: [http://wubi-installer.org/images/boot-screen.jpg](http://wubi-installer.org/images/boot-screen.jpg) [Only is says XP instead of Vista]

If I select ubuntu from that screen, it says the .mbr file is corrupted, or something like that. If I select XP from that menu, I get a second boot screen that works. It looks a bit different then the first screen, and does not say "Windows Boot Manager" at the top.

I am not exactly sure why this is going on. I've installed Wubi and Ubuntu on 3 different computers, and have never had this problem. 

Thanks.

---

### Post by linuxguy5 on 2009-07-02
Hi,
I think I've figured out the problem. After I get passed the first boot screen, I am presented with the second screen, which works. So, I selected ubuntu from that, as I usually would. ubuntu gave me a few seconds to press escape, and I was presented with GRUB4DOS. It told me I was running Windows Vista, when I am not. (XP Home) In fact, the first boot screen I am presented with, looks like the one I am running on Vista.

Does anyone know how to remove the first boot screen? Perhaps this is a bug in wubi.
Thanks.

---

