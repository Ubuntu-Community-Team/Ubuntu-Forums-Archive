---
title: "fish has stopped recording history"
date: 2010-05-21
forum: General Help
---

### Post by fishexe on 2010-05-21
I use the friendly interactive shell, or fish, as my default shell.  I find it much more user-friendly than bash, but lately (as in for the last 2 months, give or take) it has stopped adding new entries to .config/fish/fish_history and .config/fish/fish_history.tmp.  this means when I press up I don't get the last command I typed, but rather the last command from before the bug occurred.  I have no idea why this could be and have tried several tricks but none of them have worked.  I have made a bug report on launchpad ([https://bugs.launchpad.net/ubuntu/+source/fish/+bug/583543](https://bugs.launchpad.net/ubuntu/+source/fish/+bug/583543)) but I was hoping someone here who knows more about shells would know a workaround.

The things that I have tried:
removing the files to see if it creates a new one
making sure I have write access to the files
removing the files and then using touch to create a blank one

---

### Post by durand on 2010-05-21
Does it work in another user account?

---

### Post by fishexe on 2010-05-24
Yes.  I don't know what is different between the two accounts, but my main account has this problem while my other account updates .config/fish/fish_history normally.  Do you have suggestions for what to check that could explain this difference?

---

### Post by durand on 2010-05-24
Hmmm. You could maybe email the developer? :S I'm not sure really. Try changing the shell back to bash, then run fish inside it and see if you still get that problem. Just a guess at debugging. I'm not really an expert in this but I think it might be a fish-specific problem for whatever reason.

---

### Post by fishexe on 2010-11-27
As of late last month this problem has automagically fixed itself.  I'm guessing it was fixed upstream and just came out in the maverick updates.

---

