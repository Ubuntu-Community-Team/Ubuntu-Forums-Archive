---
title: "Do not show window content while dragging"
date: 2011-04-18
forum: General Help
---

### Post by PCaddicted on 2011-04-18
How can I set Ubuntu 10.10 not to show window contents while the window is being dragged?I just want to save a higher amount of system resources

---

### Post by searchfgold6789 on 2011-04-19
I would check under 'Desktop Effects'. There may not be the specific one you mentioned, but turning Desktop Effects off will save alot of system resources (especially your GPU).

---

### Post by PCaddicted on 2011-04-19
I right-clicked the background,chose "Change desktop background" and set visual effects to none,but window content is still shown while dragging.
Any suggestions?

---

### Post by CowzRule on 2011-04-19
Hit "ALT+F2" type in "gconf-editor" hit enter. Go to "apps/metacity/general". Look for "reduced_resources". A "mark" in the box makes it "true"

"If true, trade off usability for less resource usage"

"If true, metacity will give the user less feedback by using wireframes, avoiding animations, or other means. This is a significant reduction in usability for many users, but may allow legacy applications to continue working, and may also be a useful tradeoff for terminal servers. However, the wireframe feature is disabled when accessibility is on."

---

### Post by PCaddicted on 2011-04-19
Your tip worked.Thank you very much,CowzRule.

---

