---
title: "Printing from the command line won't work"
date: 2009-08-31
forum: General Help
---

### Post by ronzo on 2009-08-31
On a machine (which is around 300 km away, so I connect via SSH) running Ubuntu Jaunty 32bit I try to print a pdf document using the command:

$ lpr test.pdf 
lpr: cannot connect to X server 

WTF? Since when is X needed for LPR?

When I try the same thing at home (64bit Jaunty, different printer) it works flawlessly?

Any help would be greatly appreciated!

---

### Post by ronzo on 2009-08-31
Solution:
I used "lp test.pdf" instead of lpr...

That site led me to this solution:
[http://wiki.answers.com/Q/What_is_the_conceptual_difference_between_the_lp_and_lpr_commands_in_Unix](http://wiki.answers.com/Q/What_is_the_conceptual_difference_between_the_lp_and_lpr_commands_in_Unix)

---

