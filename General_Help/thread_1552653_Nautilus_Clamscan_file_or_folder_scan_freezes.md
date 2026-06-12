---
title: "Nautilus Clamscan file or folder scan freezes"
date: 2010-08-13
forum: General Help
---

### Post by inameiname on 2010-08-13
I decided to check out nautilus-clamscan, in which all it does is add an option to scan the selected file or folder for viruses in the context menu, and while it works fine for some things highlighted, for some that I've randomly tried it freezes, and won't complete scanning.

Not sure why. Anybody have this issue, or know why? Oh, and using the usual method of scanning for viruses through Clamtk, it scans those files and folders just fine, so it's not those themselves that's causing the freezing.

---

### Post by Ubuntist on 2010-08-19
I have the same problem and, alas, have no solution to offer.  I have posted a question on [http://launchpad.net/nautilus-clamscan](http://launchpad.net/nautilus-clamscan), and I'll let you know if I get any answer.

---

### Post by inameiname on 2010-08-19
Cool. Thanks. Hopefully they'll have something figured out. Clamtk's nautilus context menu option works well enough, so I guess it'll work if need be since this one doesn't work. But it'd be cool to figure out why it's freezing.

---

### Post by Ubuntist on 2010-08-26
Still no answer to the question I posted on launchpad.  In the meantime, though, I downloaded an [EICAR test file]("http://www.eicar.org/anti_virus_test_file.htm") just to test ClamScan.  Since I've installed the FireClam in FireFox, I got a warning after downloading the file.  That's good.  Then I scanned the file from the right-click menu: I did *not* get a warning about a possible virus.  That's bad!  Then, I opened ClamScan from Applications | Accessories and scanned the file.  I got a virus warning, as I should have.

Bottom line:  **running ClamScan by right-clicking doesn't do anything at all!**

---

### Post by inameiname on 2010-08-26
Strange. I don't get why in the world it'd be any different with scanning through whatever means and not turn up the same result. The engine is the same. :P

Well, maybe with a couple added posts here SOMEBODY will help to better clarify.

---

### Post by kainalu on 2010-10-12
I am experiencing the same problem as above.

---

### Post by inameiname on 2010-10-13
Yeah, I never got it working, either. Though, I haven't tried it in Maverick, and ever since the latest Clamav was released. I'll have to do it and get back with all of you.

---

### Post by inameiname on 2010-10-13
Okay, so I tried it in Maverick, using the latest Clamav, and sadly, the same results. 

It did seem to be working a little bit better, in which it didn't freeze as often, but it still did, even to the point of completely freezing Nautilus.

---

### Post by inameiname on 2011-06-18
Anybody ever figure this issue out. Although, I haven't tried it on Natty, so who knows, it might work now.

---

