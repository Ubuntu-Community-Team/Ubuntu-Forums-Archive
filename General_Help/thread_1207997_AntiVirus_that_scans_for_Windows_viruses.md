---
title: "AntiVirus that scans for Windows viruses?"
date: 2009-07-08
forum: General Help
---

### Post by Roasted on 2009-07-08
I have my Ubuntu rig set up with Samba. It comes in handy as a backup service for the other XP computers in the house, along with a secondary location to back up data on computers I work on. Right now I'm dealing with a Vista laptop that is smothered in viruses. I routed to my server and dumped their stuff in a folder I created on my computer.

Now, we all know Windows viruses don't effect Linux computers. However, is there a virus scanner I can use on my Linux machine to scan the Samba shares so I can make sure the files are virus-free before pushing them back to a fixed laptop?

---

### Post by wojox on 2009-07-08
You could try ClamAV with samba-vscan.

---

### Post by Roasted on 2009-07-08
I installed "Virus Scanner" from add/remove programs. It said in the description it was a GUI front end for Clam Anti Virus. But I have no flipping idea how to use it.

I go to update signatures. It gives me two buttons. Update. Close. I click update, nothing happens. I click close, it closes it.

Gah.. how do I use the darn thing?

---

### Post by hibliss on 2009-07-08
Read the man page. It will tell you how to scan from the command line.

---

### Post by Roasted on 2009-07-08
What's the command? man clamav finds nothing...

---

### Post by M4rotku on 2009-07-08
the command to scan for viruses is 'clamscan', but first you will want to update your virus definitions using 'freshclam' and then be sure to read the 'clamscan --help' because you will definitely want to customize the command to scan recursively and other such specifications.

---

