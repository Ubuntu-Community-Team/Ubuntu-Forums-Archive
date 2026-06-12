---
title: "CD .exe File under wine"
date: 2010-06-21
forum: General Help
---

### Post by kliffs on 2010-06-21
Hello, 
I have an old video editing program install CD and would like to try to use it under wine. There is a setup.exe file that i need to run but i don't have permission to run it or to give myself permission as it is on a read-only CD. This seems to be a flaw in Ubuntu unless there is something obvious that i'm missing. It is not a huge deal, the program itself is seven years old so i will throw it away if it wont work.

---

### Post by dim3000 on 2010-06-21
> **kliffs said:**
> Hello, 
I have an old video editing program install CD and would like to try to use it under wine. There is a setup.exe file that i need to run but i don't have permission to run it or to give myself permission as it is on a read-only CD. This seems to be a flaw in Ubuntu unless there is something obvious that i'm missing. It is not a huge deal, the program itself is seven years old so i will throw it away if it wont work.

What happens when you run it with wine?

---

### Post by Serpher on 2010-06-21
Run "sudo nautilus" then try.

---

### Post by yetiman64 on 2010-06-21
Try this,  in wine configuration go to the "drives" tab and add a new drive letter and point it to the cdrom folder under Linux. Then insert the cd and try opening the exe with wine.

Note that wine doesn't automatically "see" the cd drive.

Edit: @Serfer, nautilus is a graphical app and should be used with "gksudo" (check out Link #4 in my sig, scroll down the page a bit to "Graphical Sudo" section for further explanation).

@ OP, not so sure my suggestion above will change too much for you, but may be worth checking out. (It is a step I usually take to allow easy cd access in wine programs/dialogs etc).

Edit 2: Another thread very similar to your problem is [ --here--]("http://ubuntuforums.org/showthread.php?t=1514122") and seems to offer a better fix suggestion re permissions and cds particularly posts #2 & #4.

---

