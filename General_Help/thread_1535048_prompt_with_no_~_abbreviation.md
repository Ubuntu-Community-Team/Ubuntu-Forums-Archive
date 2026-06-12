---
title: "prompt with no ~ abbreviation"
date: 2010-07-20
forum: General Help
---

### Post by johntkucz on 2010-07-20
How do I change the prompt so that ~ is NOT abbreviated as home?  \w and \W, if the working dir is home, will print ~, I want it to alwasy print the full working dir path.  thanks.

---

### Post by dcstar on 2010-07-21
> **johntkucz said:**
> How do I change the prompt so that ~ is NOT abbreviated as home?  \w and \W, if the working dir is home, will print ~, I want it to alwasy print the full working dir path.  thanks.

Edit your .bashrc file.

Change the ${PWD/$HOME/~} to ${PWD}

---

