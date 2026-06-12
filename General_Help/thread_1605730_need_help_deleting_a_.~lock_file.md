---
title: "need help deleting a .~lock file"
date: 2010-10-25
forum: General Help
---

### Post by M0GEJ on 2010-10-25
I have tried sudo nautilus but cannot delete this file off my memory stick.  Any ideas?

---

### Post by coffeecat on 2010-10-25
Do you have Open Office open with a file open? Close it. It's a (hidden) file created by OO to lock an open file. The .~lock file will disappear when you close the file or close OO.

---

### Post by M0GEJ on 2010-10-25
ooo is closed at the moment.  The computer turned itself off due to low battery the other day just after I saved the file: could that be the issue?

---

### Post by coffeecat on 2010-10-25
Could be. In which case I'm surprised you can't delete the file. What filesystem is on the memory stick, FAT32 or a Linux filesystem?

---

### Post by M0GEJ on 2010-10-25
I assume the memory stick is FAT32, put it doesn't say in properties.  Managed to delete the .~lock file when I booted up into vista *shudders*, but still am unable to open the original file.  Oh well!: I guess that is one of the perils of using a laptop with a 20 minute battery life!!!

---

### Post by coffeecat on 2010-10-25
How curious. I was going to suggest opening OO and then opening the file that the lock file referred to, and finally closing OO gracefully (that is without a power failure) and seeing if that got rid if the lock file. Let us know what happens when you try to open the referred file again.

I'm at a loss to understand how a file could be locked to Linux on a MS filesystem. I'm curious to know the explanation. Interesting.

---

### Post by M0GEJ on 2010-10-25
me too.  I hope I can sort it as it will not be easy to start the coursework again.  If I sort it I shall post the solution.  Thanks for your help:)

---

### Post by M0GEJ on 2010-10-25
Solved!!!!

I renamed a found.000 file created when I plugged the memory stick into Vista to have the .odt file extension.  This opened fine and I was able to re-save the file.

That was far to much like hard work trying to figure this one out!!!!

---

