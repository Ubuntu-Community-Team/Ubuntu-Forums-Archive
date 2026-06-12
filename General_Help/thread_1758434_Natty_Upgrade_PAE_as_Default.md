---
title: "Natty Upgrade PAE as Default"
date: 2011-05-14
forum: General Help
---

### Post by jrsutton on 2011-05-14
When upgrading from 10.10 on my machine, Natty set the default boot image as 2.6.38-8-generic-pae, which didn't boot (stuck at the start image: ubuntu logo with 5 red circles). I can boot to 2.6.38-8-generic if I go into previous versions. Everything, best I can tell, works fine after doing this. I'm a complete idiot when it comes to Ubuntu. How can I uninstall/remove the 2.6.38-8-generic-pae image since it clearly doesn't work? Why would it have set this as my default image in GRUB? How can I set the normal image as default in GRUB?

---

### Post by lithopsian on 2011-05-14
You don't have to remove it, but if you want to just go into your package manager and purge it.

Do you need PAE?  Which CPU do you have and how much RAM?

---

### Post by jrsutton on 2011-05-14
I have an Intel Core i7-930 Bloomfield 2.8GHz LGA 1366 130W Quad-Core Desktop Processor with 6 gigs of ram.

---

### Post by lithopsian on 2011-05-14
So have you installed a 64 bit kernel?  That would be the best solution for your hardware.

The PAE is a 32 bit kernel adapted to address extra RAM.  I'm not sure why it wouldn't work for you, but I doubt you want to go down that road since you have one that works.

Just make sure you are actually seeing all your RAM.

The default Grub entry can be set in various ways.  Probably the simplest for you, if you still need to do it after removing the non-working kernel, is to edit /etc/default/grub and set the GRUB_DEFAULT variable.  You can set it to the name of the kernel you want to boot, or to a number indicating the default entry in the list, or to "saved" which means it always defaults to the entry you last booted to.

---

### Post by jrsutton on 2011-05-14
Sounds like I probably should try the 64-bit version. According to the Ubuntu System Monitor only 2.4 GiB of memory are showing up... On previous versions of Ubuntu I wasn't aware of a PAE switch, but I also never checked to see how much ram was showing either. I'm betting it has never been utilized properly.

---

### Post by jrsutton on 2011-05-19
Just to give a final update in case anyone reads this. Using the 64 bit 11.04 version worked perfectly. I have had no further issues. The 32 bit version also works perfectly on my Acer em250 netbook.

---

