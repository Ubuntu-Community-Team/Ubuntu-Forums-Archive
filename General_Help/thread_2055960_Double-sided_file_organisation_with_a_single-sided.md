---
title: "Double-sided file organisation with a single-sided scanner ADF?"
date: 2012-09-10
forum: General Help
---

### Post by Vot Musik on 2012-09-10
Hi all,

I've been searching around for a solution to this one, but nothing much has come up.  Would really appreciate it if someone could suggest a program or more imaginative solution for what I'm trying to do.

I have a very large pile of double-sided A4 pages to scan, and an Epson BX305FW to do it on.  The problem is that it's a home all-in-one unit, and so doesn't have a double-sided scanner to go with the ADF.

If I scan a batch of five two-sided pages by putting the batch in the ADF, pressing scan, and then flipping the batch over and repeating, the result comes out like this:

img01.jpg - side 1
img02.jpg - side 3
img03.jpg - side 5
img04.jpg - side 7
img05.jpg - side 9
 - flip - 
img06.jpg - side 10
img07.jpg - side 8
img08.jpg - side 6
img09.jpg - side 4
img10.jpg - side 2

Is there scanning frontend that would collate these correctly and save them in the right order?  I've tried simplescan, gscan2pdf, and skanlite, but none have that functionality.  Failing that, is there a file management utility that I could use to quickly rename the files to a common pattern (i.e. first sides to odd numbers, second sides to even)?  I've had a look at the [Mass Rename script]("http://ubuntuforums.org/showthread.php?t=1632248") for Nautilus, but it crashes out with a failure message.

I'm using Precise, if that helps.

Many thanks,

Vot Musik

---

### Post by Vot Musik on 2012-09-11
Quick bump - any ideas?

---

### Post by newb85 on 2012-09-11
Are you sure gscan2pdf doesn't have that functionality?  I've successfully used it in 12.04 to do exactly what you're describing.

---

### Post by Vot Musik on 2012-09-11
> **newb85 said:**
> Are you sure gscan2pdf doesn't have that functionality?  I've successfully used it in 12.04 to do exactly what you're describing.

How dense of me, you're right.  It hadn't occurred to me to use a negative value for "Increment" to renumber from the bottom up.  Have just tried it, and it works fine.

Many thanks for the help, newb85! You've saved me many hours of worthless manual renaming. Much appreciated - thread marked as "solved".

---

### Post by newb85 on 2012-09-11
> **Vot Musik said:**
> How dense of me, you're right.  It hadn't occurred to me to use a negative value for "Increment" to renumber from the bottom up.  Have just tried it, and it works fine.

Many thanks for the help, newb85! You've saved me many hours of worthless manual renaming. Much appreciated - thread marked as "solved".

Glad it worked.

---

