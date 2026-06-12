---
title: "How to prevent automatic mounting of USB drives"
date: 2011-10-11
forum: General Help
---

### Post by Paddy Landau on 2011-10-11
Do you know how to prevent the system from automatically mounting a USB drive when it is inserted?

My searches provide results that don't seem to be valid for 11.04.

---

### Post by mikewhatever on 2011-10-11
In gconf-editor, navigate to /apps/nautilus/preferences, uncheck media_automount box.

---

### Post by Paddy Landau on 2011-10-11
Thanks, Mike, but Unity does not uses gconf-editor. It uses dconf-editor instead, which does not seem to have a Nautilus option.

EDIT: I am incorrect. See next post.

---

### Post by Paddy Landau on 2011-10-11
Scratch my last reply. I'm sorry, I was given incorrect advice. Your solution worked!

Thank you.

---

### Post by mikewhatever on 2011-10-11
You are right, Unity doesn't, but Nautilus in 11.04 does. I should have mentioned the you might need to install gconf-editor.

---

