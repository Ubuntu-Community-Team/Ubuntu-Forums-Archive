---
title: "Update Manager Auto check?"
date: 2009-10-15
forum: General Help
---

### Post by daldude on 2009-10-15
Is there a way to make update manager automatically check for updates every day? When I first started using Ubuntu I thought I remembered seeing a setting in update manager to have it check for updates automatically and how often but now I can't seem to find it. 
Is it possible that I dreamed this or maybe it was in a different version or Ubuntu?
I have 8.04 32-bit.:)

---

### Post by Johnny B on 2009-10-15
system > administration > software sources > update tab

but it doesn't show the update icon in the system tray when there are updates available. This is because the update system was changed with jaunty.

If you want to use the old update manager behaviour, open a terminal and paste this:
> gconftool -s --type bool /apps/update-notifier/auto_launch false

---

### Post by fragos on 2009-10-16
> **Johnny B said:**
> system > administration > software sources > update tab

but it doesn't show the update icon in the system tray when there are updates available. This is because the update system was changed with jaunty.

If you want to use the old update manager behaviour, open a terminal and paste this:

I looked at those parameters with the "Configuration Editor" and became confused by the descriptions which implied to me that that the parameter need to be checked as true. I also saw that the install had set my update cycle to 7 days. I was accustomed to 1 day so I changed it. At 7 it only would have checked for repository updates once a week which made me assume it wasn't updating repositories. Perhaps the OP had the same problem.

---

### Post by Kangarooo on 2011-01-25
> **fragos said:**
> I looked at those parameters with the "Configuration Editor" and became confused by the descriptions which implied to me that that the parameter need to be checked as true. I also saw that the install had set my update cycle to 7 days. I was accustomed to 1 day so I changed it. At 7 it only would have checked for repository updates once a week which made me assume it wasn't updating repositories. Perhaps the OP had the same problem.
Yes thats strange. I also want to understand what is what.
Where can i with** command line **change to be automatically chacked updates every 4 weeks and on check they automatically beeing installed?

---

### Post by Frogs Hair on 2011-01-25
System > Administration > Update Manager> Settings tab auto checks and installs but only allows you to check up to every two weeks .

If want to check once a month I think you may have to write a script for that.

---

