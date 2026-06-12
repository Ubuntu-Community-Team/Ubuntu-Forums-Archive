---
title: "No &quot;Me Menu&quot; after upgrade to Lucid Lynx"
date: 2010-08-23
forum: General Help
---

### Post by alayahlan on 2010-08-23
I just upgraded my laptop from 8.04 to 10.04. Everything seems to be working well, except I don't have the "Me Menu" on the right side of the screen. I still have the same red square power icon I've always had. 

Is there a preference somewhere I need to change to get the Me Menu, or did something go wrong in my upgrade?

---

### Post by davidmohammed on 2010-08-23
right click on the panel and choose add to panel.  Scroll down and add both "indicator applet" and "indicator applet session"

---

### Post by alayahlan on 2010-08-23
Doing that gives me a "No Indicators" icon and an envelope for email and IM, it doesn't change the red power button to my login name or give me any options to access Ubuntu One or anything else the "Me Menu" has.

---

### Post by davidmohammed on 2010-08-23
using administration - synaptic manager, check that you have the following packages installed.

indicator-me
indicator-sound
indicator-session
indicator-applet-session
indicator-applet

---

### Post by alayahlan on 2010-08-23
Those were not installed. Added those and I was able to add the Me Menu. Thank you.

I was perplexed why my upgrade to Lucid didn't have it when my clean install on another computer did.

---

