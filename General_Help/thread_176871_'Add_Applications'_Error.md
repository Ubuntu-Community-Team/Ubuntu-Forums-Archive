---
title: "'Add Applications' Error"
date: 2006-05-15
forum: General Help
---

### Post by adamgfry on 2006-05-15
I am new to ubuntu, had it about a day now. When i go onto add applications on the applications menu, it comes up with an error, it says:

Unable to get exclusive lock


I would really apprectiate help as i am a n00b to ubuntu.

---

### Post by iand675@gmail.com on 2006-05-15
Generally you will get that error if you have more than one thing at a time trying to access any repositories. For example, if you have synaptic open at the same time as you have the add applications function open, it won't let the second one opened get a lock. So close out one or the other, and make sure you don't have anything installing from a deb file in the terminal.
Hope that helps.

---

### Post by adamgfry on 2006-05-15
how do i do that?

---

### Post by iand675@gmail.com on 2006-05-15
[QUOTE=adamgfry]how do i do that?[/QUOTE]
not too hard. If you see that only one of those windows at a time is open, then it shouldnt be a problem. If that doesn't work, go to a terminal Applications->terminal, then type
```
sudo apt-get dist-upgrade
```
That should hopefully fix any bugs that may be causing the problem. Otherwise, You may need to ask someone else.

---

