---
title: "A question about the Dapper install beta"
date: 2006-05-03
forum: General Help
---

### Post by djsroknrol on 2006-05-03
I finally got a DL of the Dapper beta install, and wondered if anyone knew if it could be installed over my current copy of Breezy, would it retain my current settings and programs from Breezy and would it be advisable to go that route or do a fresh install....I'm weighing my options and would appreciate any input...

---

### Post by Sef on 2006-05-03
Did you make a separate home partition?

If yes, then you can keep you home partition and everything on it.

If no, then you you will lose everything that you have saved.

In either case, **back up** your data before you install Dapper.  Things do go wrong at times and you could lose your data on your home partition.

---

### Post by djsroknrol on 2006-05-04
Hi sef...

Well, no..I didn't make a separate /home, so that's toast. However, there's nothing really important there...how about the rest of my breezy install and my settings?...any other input there?

---

### Post by djsroknrol on 2006-05-04
Sorry for the bump here...

I still am trying to learn if the install will effect any of my current programs and settings beside my losing my /home..

Does anyone have any input on this?

---

### Post by ZylGadis on 2006-05-04
If you install on top of Breezy, you'll lose everything you don't save.
If, on the other hand, you update from Breezy, no harm done. To update you need to open your sources.list file (or Synaptic) and replace all "breezy" with "dapper". Then, if you don't feel like downloading, you can put in a new repo, being your cd (if you haven't deleted the old one, which comes when breezy is installed, and which I immediately removed on all my machines), and just update from it.
Good luck, and I hope I haven't been too unclear :)

---

### Post by djsroknrol on 2006-05-04
Thanks ZylGadis..

I think I'm following you...I'm better off upgrading than installing over, correct?..if that's the case, if I update, will it include the complete beta at the point that I upgrade?..if not, I'm considering triple booting it on my hdb to play with it until the final comes out next month...

---

### Post by ZylGadis on 2006-05-04
In order to include absolutely everything from the beta, you need to install a package called ubuntu-desktop. If you have it in Breezy, it will just get updated with the rest. If you don't have it, though, you need to install it - preferably before the mass update, but no harm done if you do it afterwards - the result will be the same, but you'll spend more time and network traffic.

P.S. ubuntu-desktop is for Ubuntu Breezy and Ubuntu Dapper. You need kubuntu-desktop for the Kubuntu (KDE) flavor, and xubuntu-desktop for the XFCE one.

---

