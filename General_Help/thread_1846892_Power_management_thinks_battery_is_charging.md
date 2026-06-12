---
title: "Power management thinks battery is charging"
date: 2011-09-19
forum: General Help
---

### Post by mbroshi on 2011-09-19
I'm running 11.04 and recently my computer thinks it is charging (even when  it is not).  One particularly annoying downside is that my computer will shut off without notice if it runs out of battery (even though it is set to hibernate, although that is possibly another problem).  The Gnome Power Management icon says that the battery is charged, even though it is not.  Output of ACPI -ab  at this moment (without AC adapter attached) is: 

Battery 0: Unknown, 68%
Adapter 0: on-line

whereas with adapter plugged in it says

Battery 0: Charging, 68%, 00:52:39 until charged
Adapter 0: on-line

Any thoughts on how to fix this?

---

