---
title: "How to install Ubuntu to flash drive?"
date: 2011-08-06
forum: General Help
---

### Post by de_dust on 2011-08-06
G'day

I'm trying to install Linux to one of my flash drives. The installation goes fine until I am at the end where I get a bootloader error.

Anyone have a tutorial they can point me to?

---

### Post by Nithogger on 2011-08-06
to be sure: you are pointing to the isntallation of Ubuntu it self right? I think I know what's wrong. I _think_ I had the same problem ( it was some months ago when my laptop had a new HDD placed) If a company repaired your computer, or you bought a new one, then there might be a configuration in the BIOS. This configuration makes sure you can't install other OSs. So you have to deactivate that one. 
Once you get into the BIOS. I think it's the Main/SATA Configuration. There you see a Hard Disk Write Protect section. I suspect that that's put to 'Enable'. If so: change to Disable. Restart the whole thing and it might work. 

If you haven't got a SATA.. then I can't help you any further. 
But if you do have sata and this didn't help you, feel free to contact again and we'll work something out, somehow ;)

Cheers

---

### Post by nrundy on 2011-08-06
you are trying to set up a usb so you can use it to boot ubuntu?

Just go here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) and follow the directions.

are you saying you did this and you keep getting bootloader error when trying to boot to the live ubuntu?

---

