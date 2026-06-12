---
title: "Recovering Files from Windows Using a Ubuntu Live CD"
date: 2009-10-03
forum: General Help
---

### Post by Ziraleet on 2009-10-03
My windows XP computer recently stopped working properly, it won't start for me. So I downloaded Ubuntu onto a CD and I was trying to recover my files using it and going through [[this guide]("http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/")].
However, when I get to the step where it tells me to go to Places > Computer on the menu, that's where this problem occurs. I click on Computer, and nothing opens. I tried clicking on Desktop and Documents and Pictures, etc., but none of them will load for me.

Why is this happening and how do I fix this?
Thanks in advance.

---

### Post by oldfred on 2009-10-03
My first suspicion is that it is a bad CD. Did you burn it at the slowest speed possible? If the problem is not just your XP drive but something in the computer itself then that may be another problem.  

If you get it going and still cannot mount the HD try testdisk. It is on some live CD's or can be downloaded from synaptic.

---

### Post by earthpigg on 2009-10-03
if you burn another CD and are still having problems accessing the hard drive, i would remove the hard drive from that computer, put it in another, and try pulling the data from it there.

(well, while you have the computer case open you may as well ensure all the cables are firmly seated before you remove anything. cables can come lose, say, if you moved the computer from point A to point B in a car bouncing around.)

why?

maybe the problem with the motherboard or some other piece of hardware ***besides*** the hard drive. putting the hard drive in hardware you ***know*** to work could solve that and allow you to recover your data.

+1 to testdisk. its a professional grade low-level tool that i have had amazing results with. if putting hte HD in another computer doesn't allow you to get your data (ie: the hard drive is corrupted) then give testdisk a try.

after installing it (and you can do this on the Live CD),

1) read the wiki carefully! [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
2) open a terminal and run 'sudo photorec' and 'sudo testdisk' and see what you can do. testdisk comes with both, use photorec before testdisk.... photorec will try to recover without changing anything on the hard drive.

post back if you have any more questions.

---

