---
title: "External HD not recognized."
date: 2010-03-18
forum: General Help
---

### Post by Screatch on 2010-03-18
I am running Ubuntu 10.04 beta 1 from "testdrive", everything works okay except that it wont recognize my external firewire Seagate Freeagent drive... It worked perfectly well in Ubuntu 9.10, it detects my other internal NTFS drive but whenever i try to run gparted to see if its connected.. i don't see it, i try and run it via terminal and i see an error 

> Error: Error opening /dev/sdc: No such device or address

lsusb output does not show the drive.. What could be the problem and how to fix it?

---

### Post by audiomick on 2010-03-18
Fire wire drivers not included in the Beta yet???

---

### Post by Screatch on 2010-03-18
So.. what do i have to install to get it working?...

---

### Post by Screatch on 2010-03-19
Up... My external HD is pretty much important to me and it need to get it working...

---

### Post by pingu1 on 2010-03-19
Isn't it fstab and mtab which are the files that control mounting of drives/devices?
Could it be a problem with these? (I'm a noob)...

---

### Post by pingu1 on 2010-03-19
Can you mount other types of hardware? Usb-stick... example...

---

### Post by Screatch on 2010-03-19
USB stick mounts perfectly well, without any questions.

---

### Post by Screatch on 2010-03-19
I done a small experiment right now..
With my hard drive i had USB cable going too, so i have connected it right now using USB instead of Firewire, and guess what.. it works.

So problem must be somewhere in the firewire drivers...

However this is rather a temporary solution than a permament, so i am still looking for a solution to a firewire problem.

---

### Post by Screatch on 2010-03-19
For the people thinking it could be because i downloaded not an official beta 1, i had redownloaded and installed ubuntu again, same problem..

Works on USB, doesn't on firewire...
I guess i should file a bug.. Where can i do this?

---

