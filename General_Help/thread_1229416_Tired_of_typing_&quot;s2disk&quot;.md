---
title: "Tired of typing &quot;s2disk&quot;"
date: 2009-08-02
forum: General Help
---

### Post by Lockheed on 2009-08-02
Every time I want to hibernate, I need to open a terminal, type "sudo s2disk" and then my admin password.

How can I make a desktop icon which will hibernate with just one click?

---

### Post by DeMus on 2009-08-02
> **Lockheed said:**
> Every time I want to hibernate, I need to open a terminal, type "sudo s2disk" and then my admin password.

How can I make a desktop icon which will hibernate with just one click?

Right-click your desktop and choose Create launcher.
Give it a name, like sleep. Type s2disk in the field which says Command and comment it as you please.
Now this should do the trick.

---

### Post by Lockheed on 2009-08-02
Nope. I click it and nothing happens.

---

### Post by DeMus on 2009-08-02
> **Lockheed said:**
> Nope. I click it and nothing happens.

And when you choose at the top of the creating launcher window: Application in Terminal?

---

### Post by Lockheed on 2009-08-02
Same thing.

---

### Post by PGScooter on 2009-08-02
probably cause of the sudo thing. Try doing ```
gksudo nautilus .
```, then navigating to desktop and doing what was said but put in "sudo s2disk" as the command.

---

### Post by Lockheed on 2009-08-02
Thanks but I cannot see an option to "Create launcher" in nautilus.

---

### Post by PGScooter on 2009-08-02
oops, me neither. Try making an executable bash script.. just make a file on the desktop. But that one line of code in, save the file, make it executable with chmod (for root and user). That might be worth a shot. I have to go, but I'll check back in a couple of days and make sure you got it figured out. If not, I will install s2disk command and figure it out with you. best of luck!

---

### Post by kerry_s on 2009-08-02
first you need to add a entry in "visudo" so you don't need to use a password, then create your launcher with the sudo command.

**%sudo ALL=NOPASSWD: /usr/sbin/s2disk**

change the "%sudo" to the group you want, just make sure your in that group or just use your user name.

i use a similar on mine, but for pm-suspend

---

### Post by Lockheed on 2009-08-02
> **kerry_s said:**
> first you need to add a entry in "visudo" so you don't need to use a password, then create your launcher with the sudo command.

**%sudo ALL=NOPASSWD: /usr/sbin/s2disk**

change the "%sudo" to the group you want, just make sure your in that group or just use your user name.

i use a similar on mine, but for pm-suspend

Great, it worked!

One more thing. How do I make my laptop to s2disk when I close the lid?

---

### Post by kerry_s on 2009-08-02
> **Lockheed said:**
> Great, it worked!

One more thing. How do I make my laptop to s2disk when I close the lid?

look in /etc/acpi, there should be a script for the lid action. back it up before you modify just to be safe. :D

---

