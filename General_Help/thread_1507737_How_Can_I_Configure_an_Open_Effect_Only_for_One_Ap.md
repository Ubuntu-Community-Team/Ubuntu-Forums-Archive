---
title: "How Can I Configure an Open Effect Only for One Application?"
date: 2010-06-12
forum: General Help
---

### Post by Joseph Schwenker on 2010-06-12
I am using Compiz, and am trying to use Animations to make only Gloobus Preview (Window name= gloobus-preview) open with one of three animations.  I have selected Horizontal Folds, Sidekick, and Zoom in Random Effects, made a new item for Open, set its duration to 200, set it to Random, and have tried everything possible to try and get only Gloobus Preview to have an animation, but nothing works.  I can get everything except Gloobus Preview to have an animation, but if I do the opposite, then nothing works.  If I set it to "any", then Gloobus Preview animates, but so does everything else.  I would like for nothing to have an open animation except for Gloobus Preview.  How can I do this in Compiz's Animations?

---

### Post by Joseph Schwenker on 2010-06-12
I figured it out.  I made a new open effect, set it to none, then entered "gloobus-preview" for the name field, then selected "or", then "invert".  This makes no windows except Gloobus Preview animate.  Then, I made a new effect, set it to Random, set it's name to gloobus-preview, and kept the default options.  Keep in mind that you manually have to enter the name in after you use "Grab" to capture the name.
I do, however, have another question.  How can I use the animations from Animations Addons?  All I see is adjustment options for them, and no way to apply them.

---

