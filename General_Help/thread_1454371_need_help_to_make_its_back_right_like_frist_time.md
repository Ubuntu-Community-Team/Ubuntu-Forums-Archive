---
title: "need help to make its back right like frist time"
date: 2010-04-14
forum: General Help
---

### Post by santosamaru on 2010-04-14
:guitar:
my case is 
1.  i want to remove the image from the booting time. 
2. the most reason is, i got problem , when installing ubuntu inside windows. i do wrong experiment that make its looks like bad. and the answer is as right like Mr. Mark Phelps answer . boot.ini ( edit its on its, but just the version .! remove or delete its. :) 
:popcorn:
thanks you very much 


best regards


santos amaru 
:guitar:

---

### Post by Mark Phelps on 2010-04-15
One of the flaws with a Wubi install in XP is that it does a very poor job of cleaning up after itself.

In XP, Wubi creates a boot entry in the boot.ini file.  IF you have extra Ubuntu entries in your OS selection menu, or if you've removed Ubuntu but still have entries there, the simple fix is to open your boot.ini file with Notepad and remove the Ubuntu entries -- but just remove those, NO OTHER LINES.

---

