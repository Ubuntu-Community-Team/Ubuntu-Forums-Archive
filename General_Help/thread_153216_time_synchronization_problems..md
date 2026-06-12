---
title: "time synchronization problems."
date: 2006-03-31
forum: General Help
---

### Post by graigsmith on 2006-03-31
hi, my clock will be fine, i have it set to automatically synchronize.  and i can leave and come back, and my time will be off. usually it will be faster. by like 30 minutes, or sometimes several hours.  i then have to go manually synchronize it.  Does synchronize sometimes fail and give the computer the wrong time?  my time zone is set to america/chicago.

i only use ubuntu on this computer.  so there shouldn't be any conflicts.

---

### Post by graigsmith on 2006-04-01
like right now, real time is supposed to be 1:17 am.. but my computer clock reads 1:40 am.

---

### Post by graigsmith on 2006-04-01
hi, i think the problem is that my computer's clock is just MASSIVELY innaccurate.

in a couple hours the computer has already lost time, and is actually 2 minutes faster.

so my computer is one more minute ahead every hour.

how often does ubuntu update the time?  and can i change the interval to update it more often??

---

### Post by Mustard on 2006-04-01
What type of motherboard are you using?

---

### Post by graigsmith on 2006-04-01
its a nvidia chipset, nforce 2 board.

---

### Post by graigsmith on 2006-04-01
hey i think i fixed it, by disabling apic mode in my bios,  (not acpi, but apic).  apic gives you more interrupts and makes that more flexible.

edit, it's been several hours now, and my clock is right on time.

---

### Post by Mustard on 2006-04-02
Well done. :)  Good work troubleshooting it.

---

### Post by chomafin on 2006-04-02
hey graigsmith, I am having what seems to be the exact same problem as your self. I also have an Nforce2 M/b  When going through my bios settings, i did not see anywhere to turn off the APIC option that you have mentioned.


I was currious if you had used an option within the bios, or prehaps a kernel switch when loading linux?

---

### Post by graigsmith on 2006-04-02
no, it was a bios option.

---

