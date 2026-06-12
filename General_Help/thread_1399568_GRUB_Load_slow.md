---
title: "GRUB Load slow"
date: 2010-02-05
forum: General Help
---

### Post by SyAu on 2010-02-05
I have Ubuntu 9.10 and when i start the PC the grub takes 10 Seconds to display the list of OSes after displaying 'GRUB Loading'. 

Is there any way to make GRUB faster to load, so that it displays the OS list quickly.

---

### Post by saturnblackhole on 2010-02-05
EDIT:sorry didnt read the op post properly i thought you were asking how to speed up the time it takes for grub to finish showing the os menu. sorry i dont know how to solve your problem.

---

### Post by thulefoth on 2010-02-05
I have a delay like this with my 9.10, too.

When I was WUBI'ized over the weekend, I spent many hours crawling through the boot-files ... at the GRUB prompt.  One of the files I viewed took perhaps several minutes to scroll off the screen - in a steady flying blur.  This file was big!

This is now GRUB2, 'course - fresh for 9.10 -  and there are differences in how the new version works that might account for the delay.  This is my first go-round, tho, so I don't know how GRUB(1) behaved.

But ... it might be normal for it to take a pause while reading some of these monster files.

There are more changes coming with GRUB2.  It is only partly implemented.  I'd take this as a sign that there might be optimization still on the todo list; that for 9.10 they got switched over, put off some issues temporarily, and have been focused on getting a nicer boot routine put together for 10.04.

---

