---
title: "Unable to enable firefox option.."
date: 2010-12-30
forum: General Help
---

### Post by karthick87 on 2010-12-30
In firefox, I try to check the box in Edit &#8594; Preferences &#8594; Advanced &#8594; General which says 'submit crash report', but everytime I  close this and open it again it remains unchecked. Why is that so?

---

### Post by mcduck on 2010-12-30
Most likely because the Firefox in Ubuntu's repositories is configured to use Ubuntu's crash reporting tools instead of the one built in by Mozilla.

Same as with updating Firefox, it's handled through same package management as every other application on your system instead of sing Firefox's own update tool.

---

### Post by karthick87 on 2010-12-30
Thank you..But is it possible to enable mozilla crash reporting tools??

---

### Post by mcduck on 2010-12-30
I can't say for sure, never seen any reason to do such things (as bugs in the Firefox from Ubuntu repositories should be reported to Ubuntu developers, not to Mozilla).

But uninstalling *ubufox* and *xul-ext-ubufox* packages might work.

---

### Post by karthick87 on 2010-12-30
If so how that option is enabled in ubuntu 10.10??

---

