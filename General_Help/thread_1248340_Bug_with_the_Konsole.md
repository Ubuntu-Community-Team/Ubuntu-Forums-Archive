---
title: "Bug with the Konsole"
date: 2009-08-24
forum: General Help
---

### Post by ProgVal on 2009-08-24
Hello,

I'm a french user of Ubuntu, and I tryed to get solution on the french support forum, but I can't get any solution.

My problem is the fellowing:
When I use the Konsole, sometimes, I want to edit the previous command. I press the "up" key, and I edit the command. But, if I put the cursor at the beginning of the command... the Konsole doesn't answer during one or two minutes. And if the cursor is on the black area, I can't see it.

I had this problem, and many other with KDE4.2, so, I installed KDE4.3. I've less problems, but this one is still here.

Thank you for advance,
ProgVal

---

### Post by P4man on 2009-08-24
I dont use KDE, but you could try a different terminal, and see if that cures it ? I'd suggest you try Yakuake while you're at it :)

---

### Post by Gen2ly on 2009-08-24
Yakuake = Konsole.

I'd report this as a bug.  Probably has to do with kpart.  Either put on launchpad, or even better the kde bugzilla.

---

### Post by ProgVal on 2009-08-24
What's "KPart"?

EDIT: Yakuake has the same bug. And when it is bugging, I can't hide it. As it take almoste all the screen, I must to wait without doing anything...

---

### Post by nikhilk on 2009-08-24
> **ProgVal said:**
> What's "KPart"?

EDIT: Yakuake has the same bug. And when it is bugging, I can't hide it. As it take almoste all the screen, I must to wait without doing anything...

KParts is a component framework for KDE. It is the building block of almost every KDE application. Take a look at [this]("http://developer.kde.org/documentation/tutorials/kparts/") developer documentation if you are interested in knowing more.

---

### Post by ProgVal on 2009-08-24
KPart is not in the Kickof menu... (maybe because I've KDE 4.3?)

---

### Post by nikhilk on 2009-08-24
> **ProgVal said:**
> KPart is not in the Kickof menu... (maybe because I've KDE 4.3?)

It is not an application itself. It is a framework that is used by actual KDE applications like konsole, koffice etc.

---

### Post by ProgVal on 2009-08-24
And how to use it?

---

### Post by nikhilk on 2009-08-24
> **ProgVal said:**
> And how to use it?

You don't have to do anything to explicitly use it. Whenever you launch an application like konsole the kparts libraries are being used behind the scenes.

It is like the C runtime library, applications automatically use it under the hood which is not directly visible to you.

---

### Post by ProgVal on 2009-08-24
Ok, I've bad understood the message #3 (I though that I had to report the bug with KPart)

---

### Post by P4man on 2009-08-24
> **ProgVal said:**
> And how to use it?

He only mentioned it, if you file a bug report, you can indicate which (likely) package is affected.

BTW, this bug seems similar, though not identical;

[http://bugs.kde.org/show_bug.cgi?id=181151](http://bugs.kde.org/show_bug.cgi?id=181151)

---

