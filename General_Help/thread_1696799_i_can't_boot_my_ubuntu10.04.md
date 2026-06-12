---
title: "i can't boot my ubuntu10.04"
date: 2011-02-27
forum: General Help
---

### Post by wszbd on 2011-02-27
thank you for your attention

yesterday ,10.04's updating program failed,then i closed my laptop directly.
today i came across the question :
> 
no such device  blablabla                 grub rescue>
this is the second time that my computer shows this question after the updating programe faled
last time i followed  instructions  from forum and solved the question.
that seems a questiion due to mbr loss.so i do as i did last time to fix my mbr through livecd
> 
sudo apt-get install  lilo                              sudo lilo -M /dev/sda mbr
it worked at first time. i can choose the System ubuntu or xp.  it seems everything is ok.
after i entered the ubuntu,question:
 > 
try (hd0,0):extended 
try (hd0,1):ntf35
And these  Question information flashed before my eyes and  rebooted~~

anyone can help me?     thank you ~~

---

### Post by Rubi1200 on 2011-02-28
Hi and welcome to the forums :-)

How did you install Ubuntu in the first place; to a dedicated partition or with Wubi?

Your answer will determine the possible solution.

Thanks.

---

