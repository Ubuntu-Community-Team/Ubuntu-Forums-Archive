---
title: "tried using compizconfig on 11.04 and it"
date: 2011-05-24
forum: General Help
---

### Post by lance23dillon on 2011-05-24
I recently got ubuntu 11.04 on my laptop and I put compizconfig on it and had enabled some effects, then my launcher and panels disappeared. 

When I restart my computer I can still get on to the safe mode and no effects mode just fine,but the regular ubuntu still comes up as a blank desktop.

Any help with this would be great!!!

---

### Post by garvinrick4 on 2011-05-24
> **lance23dillon said:**
> I recently got ubuntu 11.04 on my laptop and I put compizconfig on it and had enabled some effects, then my launcher and panels disappeared. 

When I restart my computer I can still get on to the safe mode and no effects mode just fine,but the regular ubuntu still comes up as a blank desktop.

Any help with this would be great!!!
go into a terminal if cannot hit ctrl/alt/t and login then:
```
unity --reset
```

Always make sure in 
```
ccsm
```
The Ubuntu Unity plugin is checked.
If not installed install it.
```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by lance23dillon on 2011-05-24
Awesome, every thing is set back to normal.

Thanks

---

