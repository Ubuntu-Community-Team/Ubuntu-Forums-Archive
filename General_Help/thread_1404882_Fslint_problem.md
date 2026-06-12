---
title: "Fslint problem"
date: 2010-02-11
forum: General Help
---

### Post by JBA2337 on 2010-02-11
I was looking for a duplicate file-finder that will allow me to delete the duplicate files directly from the program. After seeing several recommendations in this forum I installed Fslint from the repositories. It easily found the duplicate files that I needed to remove.

The problem is, if I select a duplicate file and if I click on Delete at the bottom of the Fslint window, nothing happens. The duplicate files that I selected are not deleted.

I thought there might be something wrong with the repository version, so I downloaded the latest version of Fslint (v. 2.40-1), and I have the exact same problem. Fslint will not delete any files.

Maybe Fslint is being interfered with by some other program. I am using Ubuntu 9.04.

Does anybody have an idea how I can fix this?

THanks!

JBA2337

---

### Post by ydristi on 2010-02-12
try fslint as root .i hve once such problem & it wrkd 4 me

---

### Post by JBA2337 on 2010-02-12
> **ydristi said:**
> try fslint as root .i hve once such problem & it wrkd 4 me 

To: ydristi

Thanks very much for your tip. I opened a root terminal, and then typed in "fslint-gui". I was able to easily delete duplicate files. Plus it scanned my computer for duplicates much faster than when not running as root.  

Thank you. Thank you. Thank you!!!

JBA2337

---

### Post by JBA2337 on 2010-02-12
Instead of using a root terminal and manually typing in the command, I put "gksudo fslint-gui" in the Command box for the FSlint launcher.

That runs the program just as well as the manual procedure. All I have to do is click on the FSlint launcher.

JBA2337

---

