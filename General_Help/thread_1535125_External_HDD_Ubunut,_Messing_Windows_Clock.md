---
title: "External HDD Ubunut, Messing Windows Clock"
date: 2010-07-20
forum: General Help
---

### Post by Virtua-Touch on 2010-07-20
I have Ubuntu 10.04 on an external HDD which is set as SDF, and it's always SDF because I always have my USB drives plugged in. Anyways, everytime I boot into my external HDD, the time on Windows jumps ahead 4 hours. I'm not sure if it's changing the bios, so I should probably check that first, but when I sync it with Microsoft, the time goes correct, back 4 hours to where it should be. I have no idea why it's shooting ahead. Ubuntu reads the time correctly.

---

### Post by ajgreeny on 2010-07-20
I presume you live in an area that is four hours different from GMT or UTF, whichever you prefer to call it, and one of your OSs is set to GMT, the other to local time, ie four hours away from the other.

Just out of interest, what time does your BIOS show?

---

### Post by Virtua-Touch on 2010-07-20
16:11 (4:11 PM)

That's what it's reading in my BIOS. So it's right, but just not updating in Windows when I go in Ubuntu.

---

### Post by ajgreeny on 2010-07-20
Oh well, it was worth a try, but you don't say where you are.  Four hours away from GMT?

I can not help in windows at all, as I don't have it to even look at any more, and certainly can't remember how to set time or sync with ntp servers, as you can in ubuntu.

---

### Post by Virtua-Touch on 2010-07-20
Sorry, I live in East Coast USA, Pennsylvania to be exact.

---

### Post by john newbuntu on 2010-07-20
Please check the value of "UTC" in /etc/default/rcS.  If it is yes, change it to no.
You can edit the file using: gksudo gedit /etc/default/rcS

---

