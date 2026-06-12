---
title: "Printer Issues: What exactly are the Samba cache files in /var/cache/samba/printing?"
date: 2006-05-06
forum: General Help
---

### Post by ahallubuntu on 2006-05-06
I have a Ubuntu machine that is use, via Samba and Cups, as a print server for a small office.  It works fairly well except for an occasional issue that seems to be solved (by trial and error I figured this out) by removing a Samba cache file.  I'm trying to understand exactly what this file is and if I can safely remove it, perhaps nightly.

In the directory /var/cache/samba/printing, I have several .tdb files:  one is a generic file called "printers.tdb" and the others are called (for example) MyPrinter.tdb (where "MyPrinter" is the name of a printer I am sharing).  Usually, the file MyPrinter.tdb is of the same byte length as the generic printers.tdb file.  Sometimes one of our printers will simply stop responding, and   in that case the MyPrinter.tdb file is now much larger than printers.tdb .  I have found that if I delete MyPrinter.tdb, it will start working again.

Does anyone know exactly what these .tdb files are used for?  It's frustrating that I sometimes have to blow these files away just to get our printers to work again, but if I can via a Cron job erase them once a night I would start doing that.  Is there any consequence?

---

### Post by blackjack6.21.91 on 2006-05-06
if you've already been deleting it i dont think doing it to a schedule would pose any problems..

---

### Post by ahallubuntu on 2006-05-06
You are probably right, there is probably no harm in blowing away this .tdb file.  But it frustates me that I don't understand what is happening, what this file is used for, or why deleting it fixes my problem!  Maybe some insight would help me choose a better solution instead of this little band-aid.

---

### Post by r53s on 2006-05-06
Samba uses Trivial database files known as .tdb...
And it seems safe to remove them... when they are in /var/cache...

---

### Post by leototo on 2006-05-07
i have problem with scim to ubuntu 5.10 can yau help me to polish off the problem

---

