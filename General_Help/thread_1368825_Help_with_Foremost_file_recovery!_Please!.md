---
title: "Help with Foremost file recovery! Please!"
date: 2009-12-31
forum: General Help
---

### Post by ImmigrantUS on 2009-12-31
I need help with Foremost file recovery! Already tryed Photorec but did not find lost photos... 
 Now trying Foremost running of Ubuntu Rescue Remix live CD (CLI interface) to recover deleted photos from main (sda2) HD, using additional internal HD (sdb2) for putting recovered files into it (has 15 GB available space). 
  First I check fdisk -l, then create Foremost directory, then mount sdb2 on it, and after that trying to run foremost.
 When I issue commands:```
 sudo foremost -v -T -t jpg -i /dev.sda2 -o /media/disk/Foremost 
```
or```
 sudo foremost -v -T -t jpg -i /dev.sda2 -o /dev/sdb2 /media/disk/Foremost 
```
 Foremost starts running but very soon gives error - not enough space... Then I don't see any Foremost directories in either drive... What am I doing wrong? What to do?

 P.s. Happy New year everyone! Wish you all well!

---

### Post by ImmigrantUS on 2010-01-01
:confused: Anyone can help??? Please.

---

### Post by sbergman on 2010-05-05
Did you perhaps make a typo in the "-i /dev......" section? It should be "-i /dev/sda2" and not the way you had it. The following should work.

sudo foremost -i /dev/sda2 -o /home/user/foremost -t all -T

Then hunt around in /home/user/foremost/foremost____TIMESTAMP/ for your lost files.

While on the topic, I should say for the benefit of whomever, that if foremost gives you a message saying that it is Processing STDIN, it means that it couldnt read your input drive and is waiting for you to type stuff in at the prompt that it can scan. Haha - that should take a while if your wanting to scan through 180Gb. Press Ctrl+D and try a different invocation.

---

