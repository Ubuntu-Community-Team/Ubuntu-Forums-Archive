---
title: "Tamper-resistant school setup?"
date: 2011-04-05
forum: General Help
---

### Post by Some One on 2011-04-05
I work in a school. A common problem here is that younger students love messing desktops up. In Windows, this problem can be solved particularly by restricting the access to the control panel. But I think that Ubuntu, which is our currently used OS, can provide a greater control over student PCs. In fact, I even like that they play this way, so rather than restricting it'd be better for me to undo their changes later. The versions are 9.04 to 10.04, but it's not a constraint.

So yes, I would like to have a fresh user environment after the boot. The solution should not go too far, e.g. boot-stage image cloning, and there must be a possibility to install and keep installed new software. As you could guess, I'm not experienced in Linux, but I do know the basics and I have some programming skills (c/c++/c#, windows). I don't know where to start. Is there a folder or files one can erase to get a fresh user profile? May be there is a solution already?

Cheers!

---

### Post by Joe of loath on 2011-04-05
Simply restrict the permissions of the student logins so they can't mess with the administration options, no access to the terminal etc.

---

### Post by Grenage on 2011-04-05
It sounds like you might be after a kiosk mode?

---

### Post by Some One on 2011-04-05
Ok, now I have something to google for :) Thank you. But what with self-restoring profiles? As I said, it's a preferred option.

---

### Post by Grenage on 2011-04-05
I can't see any reason why an rc script couldn't delete a profile, and move a copy into its place; it would be a pretty simple script.

I am sure others can and will come up with a more elegant solution.

---

