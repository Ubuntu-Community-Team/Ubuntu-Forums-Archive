---
title: "Print out from GIMP in A3"
date: 2010-03-12
forum: General Help
---

### Post by clyne on 2010-03-12
I have scanned architectural A3 drawings in to my pc from my Brother MFC A3 printer/scanner, altered the drawings by adding notes, dimensions, etc using GIMP but cannot print back out in A3. It prints out in A4 on a A3 page. Must be a coomon problem but can't find a solution. Help please?

---

### Post by Vaphell on 2010-03-12
does the preview show a proper alignment? what happens when you scale picture dimensions manually to fill the whole area? are you sure that a3 is set in page settings as a default size?

---

### Post by clyne on 2010-03-12
> **Vaphell said:**
> does the preview show a proper alignment? what happens when you scale picture dimensions manually to fill the whole area? are you sure that a3 is set in page settings as a default size?
 
The preview shows everything OK. I've set every setting possible but no luck. PS I'm new to Ubuntu as well so apologies for delays etc.

---

### Post by ajgreeny on 2010-03-12
A brother mfc printer.scanner that I use was a problem to get the page size correctly aligned as there was a well hidden file in one of the brother folders that the driver package added, which still said **letter** instead of **A4.**  Everything else in the application being printed from and the driver from the print dialog said A$ not letter, and the paper margins were completely wrong.

It took a while to find the answer, but it was simply to edit the file /usr/local/Brother/Printer/**mfc5860cn**/inf/br**mfc5860cn**rc or /usr/Brother/Printer/**mfc5860cn**/inf/br**mfc5860cn**rc and change the word **letter** to **A4**, but it may be possible for you to change it to A3 as that is what you want.

The name of your printer will need to be used where in my filename it is shown as mfc5860cn

I hope that may do the trick for you.

---

### Post by clyne on 2010-03-24
thanks for the sugestion but I have Windows vista and aparently your fix is for linux. Someone out there must surely have the answer?...........

---

### Post by Chronon on 2010-03-24
This is a linux forum, so not sure why you're asking here?  A GIMP forum would seem more apt.

---

