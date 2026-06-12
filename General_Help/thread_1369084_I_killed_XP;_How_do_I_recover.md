---
title: "I killed XP; How do I recover?"
date: 2009-12-31
forum: General Help
---

### Post by Leach54 on 2009-12-31
last night I was attacked by at least 12 Trojans (but probably more). Like any sane person I ran a scan and disconnected my Ethernet cable. I ran two scans one on c:/WINDOWS folder and one on c:/ . My computer shut down when the scan of c:/ finished.  unfortunately i think one of them got to system 32 before i noticed or could stop it. Now when I boot XP I get the blue screen of death saying "Windows has detected a critical problem" Or something like that.

My question is "What apps or steps can I take to check the disk partition and eventually repair my XP operating system."

I wasn't sure who to talk to or where to put this but here it is, If you cant help please refer me to someone who can. And yes I relies that this is not Microsoft support but I thought id try here first.

---

### Post by bkratz on 2009-12-31
> **Leach54 said:**
> last night I was attacked by at least 12 Trojans (but probably more). Like any sane person I ran a scan and disconnected my Ethernet cable. I ran two scans one on c:/WINDOWS folder and one on c:/ . My computer shut down when the scan of c:/ finished.  unfortunately i think one of them got to system 32 before i noticed or could stop it. Now when I boot XP I get the blue screen of death saying "Windows has detected a critical problem" Or something like that.

My question is "What apps or steps can I take to check the disk partition and eventually repair my XP operating system."

I wasn't sure who to talk to or where to put this but here it is, If you cant help please refer me to someone who can. And yes I relies that this is not Microsoft support but I thought id try here first.



If nothing else Nixie is very entertaining!

[http://www.youtube.com/watch?v=9h3q5ss40oY&feature=response_watch](http://www.youtube.com/watch?v=9h3q5ss40oY&feature=response_watch)

---

### Post by Mahngiel on 2009-12-31
I ran into that a few weeks ago as well, made me realize i dont really want windows at all. So i expanded my ubuntu partition and haven't looked back.

---

### Post by lykwydchykyn on 2009-12-31
Without knowing specifics about what trojans you ran, or what you scanned with, or what your scan software did with what it found, it's a bit hard to say what you can do at this point.

How exactly do you know there were 12 trojans?  How did they "attack"?

The most effective thing to do at this point is a fresh install.  If you have an actual Windows XP disc, and not one of those "system recovery" discs you get with cheaper computers, then you can probably run a "repair install" which will reinstall the OS without removing programs or data.  But that also won't remove any malware that might still be present.

---

### Post by Leach54 on 2009-12-31
I scanned with AVG and it probably put them in "The Vault" or deleted them. I know there were at least 12 beacuse that was what it found before I had to sleep. (No seriously I would have stayed up through the whole thing if it was even remotely possible I Had to sleep) Thank on the re install but I don't thing i have one. I Have another computer that runs XP can I copy the c:/WINDOWS folder from  that into my computer? (I can do it but do you think it will work?)

I would need to save my registry. Where can I find those files?

---

### Post by ST3ALTHPSYCH0 on 2009-12-31
Can you boot into safe mode?
If you can, boot into safe mode with networking. Then, download and run Malwarebytes Antimalware.
Alternately, you can try running Avast or clam from Ubuntu.
If none of that works, you're looking at using Ubuntu to back up your personal stuff and reinstalling.

---

### Post by Leach54 on 2009-12-31
No I cant boot safe mode which means that the problem is in the boot files. Ill try clam. Thanks all! (if ya have any more tips send them my way)

---

### Post by kevinatkins on 2009-12-31
Another very good anti-virus toolkit is Dr. Web - you can download a live CD (Linux-based, yay), boot your computer from that and scan your windows partition (be sure to read the documentation - you need to ensure that it removes infected files as well as detecting them!)

It works well - it's got me out of jail where others (notably AVG...) have failed miserably..

---

### Post by eveningsky339 on 2009-12-31
Do you have your XP bootable disc?  A complete re-install could be in order; this sounds messy.  If there is anything you want that is left on your CD drive you could run Ubuntu from the Live CD and try to fetch them.

---

### Post by Leppie on 2009-12-31
Try images like [Ultimate Boot CD]("http://www.ultimatebootcd.com/index.html") or Hiren's Boot CD. They contain a wealth of tools that may help you get better insight on what exactly is wrong with your windows.

---

### Post by BigCityCat on 2009-12-31
> **kevinatkins said:**
> Another very good anti-virus toolkit is Dr. Web - you can download a live CD (Linux-based, yay), boot your computer from that and scan your windows partition (be sure to read the documentation - you need to ensure that it removes infected files as well as detecting them!)

It works well - it's got me out of jail where others (notably AVG...) have failed miserably..

I don't need this but this sounds very interesting. I'm uh check it out.

---

### Post by crucialhoax on 2009-12-31
Ultimate Boot CD should be able to help you as it has 3 different scanners. Since its considered an 'offline' scanner is doesn't actively use the Windows file system -- except for scanning it of course -- so that increases the removal rate if anything is found.

[http://www.ubcd4win.com/downloads.htm](http://www.ubcd4win.com/downloads.htm)

---

