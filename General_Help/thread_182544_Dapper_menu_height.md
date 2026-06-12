---
title: "Dapper menu height"
date: 2006-05-26
forum: General Help
---

### Post by mcframe on 2006-05-26
In previous Kbuntu releases it was possible to set the height of menu entries by manually adding a  ```
MenuEntryHeight=xx
``` line in the ```
[menus]
``` section of ```
~/.kde/share/config/kickerrc
```
With Dapper this is not working anymore, it seems like the kickerrc config file is overwritten by any process, simply ignoring and deleting the above mentioned line. 
Is there someone out there experiencing the same problem? 
Is this a bug or a feature?
Any hint for a solution?

Cheers mcframe](*,)

---

### Post by asimon on 2006-05-27
It's still working here with current Dapper. Did you restart Kicker with```
dcop kicker kicker restart
``` after adding the option to kickerrc?

---

### Post by mcframe on 2006-05-28
Thx asimon,
you're right, the icons of the menu entries could now be shrinked, unfortunately the spacing between the lines remain unchanged.
Any further hints?

Cheers
mcframe

---

### Post by asimon on 2006-05-30
Yes, you're right. The spacing gets bigger if you make the icons really large. But the spacing doesn't shrink beyond a certain minimum value. That minimum seems to be rather large. There is no way to configure the line spacing itself. AFAIK that is controlled by the widget style you use. Maybe there are some other styles with a smaller line spacing. Most widget styles use a bit more space between lines to increase readablility and usability... but there are many tastes when it comes to spacing.

---

