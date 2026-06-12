---
title: "Can anybody help me with these problems I have with 10.04?"
date: 2010-05-04
forum: General Help
---

### Post by TDHicks on 2010-05-04
When I updated from 9.10 to 10.04, the only thing I noticed immediately was that the Application menu and the things next to (Similar to window's Start button).
That's still gone.
I also am having problems with my hibernate.  Whether I close my lid or physically click to hibernate, all that happens is my screen goes black but doesn't shut off all the way and the power button does nothing.
Can anybody help me out here?

---

### Post by TDHicks on 2010-05-04
bump

---

### Post by lisati on 2010-05-04
> **TDHicks said:**
> When I updated from 9.10 to 10.04, the only thing I noticed immediately was that the Application menu and the things next to (Similar to window's Start button).
That's still gone.
Does right-clicking on the top panel give you an option "Add to panel"?
> **TDHicks said:**
> bump
Please be patient, we're all volunteers here. The usual guideline for bumping posts here is once per day.

---

### Post by TDHicks on 2010-05-04
> **lisati said:**
> Does right-clicking on the top panel give you an option "Add to panel"?
Yeah.  I've added the icons for Applications, games, graphics, etc. but I can't find the original drop-down menus I've grown oh-so fond of.

---

### Post by TDHicks on 2010-05-04
AH!
I found the menus!
All I need fixed now is the hibernation problem

---

### Post by tgalati4 on 2010-05-04
What you probably want is "suspend".  Hibernate justs makes a snapshot of your RAM to disk.  When you wake from hibernate, the kernel rereads the disk and fills the RAM.  This takes as long as a cold boot, so I don't use it.

Suspend keeps power to the RAM chips, so your memory stays intact.  Your system wakes in 3-7 seconds from lifting the lid.

Open a terminal:

man pm-suspend
sudo pm-suspend

Describe what happens and any error messages in the terminal.

---

### Post by TDHicks on 2010-05-04
> **tgalati4 said:**
> What you probably want is "suspend".  Hibernate justs makes a snapshot of your RAM to disk.  When you wake from hibernate, the kernel rereads the disk and fills the RAM.  This takes as long as a cold boot, so I don't use it.

I want to hibernate because my BIOS won't open up in a regular boot and only opens up when it is woken up from a hibernation.  It's how I get my sound working

---

### Post by tgalati4 on 2010-05-04
Do the above for pm-hibernate.

You need a swap file that is bigger than your RAM size:

free

df -h

---

