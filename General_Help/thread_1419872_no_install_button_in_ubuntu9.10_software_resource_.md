---
title: "no install button in ubuntu9.10 software resource center"
date: 2010-03-02
forum: General Help
---

### Post by syed.rakib.al.hasan on 2010-03-02
i just install ubuntu 9.10 in my dell laptop yesterday

i go to APPLICATIONS > SOFTWARE RESOURCE CENTER > ANY CATEGORY > ANY APPLICATION WHICH HAS NOT YET BEEN INSTALLED.......... i dont see any install button or link to install the software......

what do i do?

---

### Post by darolu on 2010-03-02
Do you get to the point depicted in the attached screenshot and no buttons at all?

You can always use Synaptic (System-Admin-Synaptic) or use the terminal:
```
$ sudo apt-get install yourpackage
```

---

### Post by mpt on 2010-03-06
> **syed.rakib.al.hasan said:**
> i go to APPLICATIONS > SOFTWARE RESOURCE CENTER > ANY CATEGORY > ANY APPLICATION WHICH HAS NOT YET BEEN INSTALLED.......... i dont see any install button or link to install the software......

what do i do?

You might find that this problem has fixed itself already. If it hasn’t:
[LIST=1]
[*]Close Ubuntu Software Center.
[*]Open Update Manager (System > Administration > Update Manager).
[*]Click the “Check” button near the bottom. (You will need to enter your password.)
[*]Close Update Manager, and reopen Ubuntu Software Center.
[/LIST]

I’m sorry we didn’t discover this problem before Ubuntu 9.10 was released. It happens only until the first time you check for updates. All the Ubuntu testers were installing updates, so they didn’t see the problem.

---

### Post by elliotn on 2010-03-06
Ja when I first opened software center I had the same thing. Somehow i did an update and it worked.

---

