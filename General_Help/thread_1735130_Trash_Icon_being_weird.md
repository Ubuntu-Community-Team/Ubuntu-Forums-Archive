---
title: "Trash Icon being weird"
date: 2011-04-20
forum: General Help
---

### Post by koolaidz83095 on 2011-04-20
I use the Awn Dock and I have the Garbage applet on it. The icon says I have one file in the trash but when I click on it, nothing appears. 

I put the default Ubuntu trash app on the top panel it also shows that there is something in the trash. Again though, when I actually click on it to open it, nothing is in there. 

This is more or less of an OCD problem but if anyone can help me fix this I'd appreciate it. 

Thanks.

::EDIT::
Added a picture for clarification.

---

### Post by Krytarik on 2011-04-21
Try this:
```
sudo rm -rf ~/.local/share/Trash/files/*
```
Greetings.

---

### Post by koolaidz83095 on 2011-04-21
Nothing happened, it still says I have one file in the trash but I still can't see it. 

Thanks though.

---

### Post by yetiman64 on 2011-04-21
If you have deleted a file on a removable drive, then removed that drive before emptying the bin that situation can occur. It has happened to me in the past.

The solution is to plug back in the removable drive, empty the bin and all should be OK.

---

### Post by koolaidz83095 on 2011-04-21
I'll keep that in mind if that ever happens again.

I say again because this problem seems to have fixed itself :?. I booted into Ubuntu this morning and my trash can was empty so it's all good now. 

Thanks for helping everyone.

---

