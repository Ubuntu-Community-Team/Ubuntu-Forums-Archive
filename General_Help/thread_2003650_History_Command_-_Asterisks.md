---
title: "History Command - Asterisks"
date: 2012-06-14
forum: General Help
---

### Post by GearLess22 on 2012-06-14
I was scrolling my history list when I found an asterisks in the history output:

[FONT="Courier New"] 2112  history
 2113  grep -i '^..j.r$' /usr/share/dict/words
 2114  grep -i '^..j.r' /usr/share/dict/words
 2115* grep -i '^..j..$' /usr/share/dict/words
 2116  cd /usr/share/dict/words[/FONT]
 
What does the asterisks mean in the history output?

---

### Post by Habitual on 2012-06-14
This variable, when set to ‘on’, causes Readline to display an asterisk (‘*’) at the start of history lines which have been modified.  This variable is ‘off’ by default.

says [http://www.gnu.org/software/bash/manual/bashref.html](http://www.gnu.org/software/bash/manual/bashref.html)

What that means is RL, I don't know. sorry.

---

### Post by GearLess22 on 2012-06-14
> **Habitual said:**
> This variable, when set to ‘on’, causes Readline to display an asterisk (‘*’) at the start of history lines which have been modified. This variable is ‘off’ by default.
 
I'd seen that but didn't quite get it because I couldn't duplicate the scenario. I've tried Ctrl-R then searching for a command and modifying it but no luck. Whatever I did to make that particular line "modified", I can't replicate.

---

