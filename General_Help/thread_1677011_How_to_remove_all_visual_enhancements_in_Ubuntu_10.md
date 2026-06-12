---
title: "How to remove all visual enhancements in Ubuntu 10.10?"
date: 2011-01-28
forum: General Help
---

### Post by Pipps on 2011-01-28
I have disabled all animations in the 'Appearance' settings.
I have checked the 'reduced_resources' option in gconf-editor > metacity > general.

But my lower-spec system is still displaying lots of unnecessary visual animations whenever I resize windows or switch screens.

How can I disable absolutely ALL visual animations?

---

### Post by HiImTye on 2011-01-28
use metacity and disable compositing, that should disable all of the major visual effects (minimizing, transparency, etc)

---

### Post by Pipps on 2011-01-28
Thanks for your input.

I have accessed /apps/metacity/general/compositing_manager and composting is already unchecked.

As I mentioned previous, reduced_resources and Appearance animations are already disabled too.

What could be the cause of all these continued unwanted visualisation enhancements?

---

### Post by dino99 on 2011-01-28
open synaptic and remove/purge all compiz packages

---

### Post by asmoore82 on 2011-01-28
"System -> Preferences -> Appearance -> Visual Effects -> None"

And Alt+F2 ...
```
metacity --replace
```

---

### Post by Pipps on 2011-01-28
> **asmoore82 said:**
> "System -> Preferences -> Appearance -> Visual Effects -> None"

And Alt+F2 ...
```
metacity --replace
```

I have already done that. Please read the first line of my first post.

---

