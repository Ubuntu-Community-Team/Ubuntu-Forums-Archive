---
title: "How to run application using command line?"
date: 2009-11-20
forum: General Help
---

### Post by teikyuen on 2009-11-20
I'm new to linux and feel want learning it. But I face problem when i want to run skype using command line. I typed "skype" in terminal then the skype is running, but when i close the terminal, the skype closed too. 

What is the command to run application like skype but it won't close even if the terminal closed? 

Thankz

---

### Post by hwttdz on 2009-11-20
You're looking to background the application, or run "skype &", I'm pretty sure there's a good terminal intro floating around as well.

---

### Post by vexorian on 2009-11-20
You may try alt-f2 to open the run dialog.

You may also add a "run" button to your panel using "right click in panel\add to panel"

hwttdz: Was going to suggest & but for some reason, for some apps closing the terminal kills the app regardless of using &.

---

### Post by teikyuen on 2009-11-21
> **hwttdz said:**
> You're looking to background the application, or run "skype &", I'm pretty sure there's a good terminal intro floating around as well.

I have tried this way, it works as I'm still able to type new command after "skype &", but when i close the terminal, it kills the app too... anyway, i learnt new thing ^^

---

### Post by teikyuen on 2009-11-21
Open run dialog is the best way, but if I insist using terminal, what would be the command? Thankz

---

### Post by lmarmisa on 2009-11-21
Try

**nohup skype &**

Best regards,

Luis

---

### Post by llamabr on 2009-11-21
Yes, nuhup is the correct solution, as it backgrounds a process even if the terminal 'hangs up'.

But, generally, if you want to close the terminal after starting, you probably don't need to open the terminal in the first place.  you can run with alt-f2, or just from the menus.

---

### Post by lmarmisa on 2009-11-21
I agree with you, llamabr.

Only one remark: the sequences for switching to one of the 6 text terminals available are "alt+ctrl+F1" - "alt+ctrl+F6". "alt+ctrl+F7" switches back to the graphical screen.

Best regards,

Luis

---

### Post by hwttdz on 2009-11-21
Interestingly closing out the terminal has different behavior than typing exit.  I always use the exit command, hence my thinking that backgrounding an application would allow it to continue running after exiting the terminal.  That's almost weird and seems inconsistent.

---

