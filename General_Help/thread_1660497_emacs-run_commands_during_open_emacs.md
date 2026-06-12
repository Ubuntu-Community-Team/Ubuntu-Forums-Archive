---
title: "emacs-run commands during open emacs"
date: 2011-01-05
forum: General Help
---

### Post by chiapas on 2011-01-05
After open emacs, I always run the following commands:

Ctrl+x 3 (split window to 2 windows, one in left, one in right, but they are the same buffer)
Ctrl+x o ( go the the right window)
M-x term ( wanna to run /bin/bash)
Enter ( to confirm the operation : Run Program: /bin/bash)

Then I get:
2 windowsl left window is the document I would like to edit (or blank document) and the right window is the term window, where I can type commands (for example, nano, cc -o...etc);

I would like to know if it is possible to add something in ~/.emacs such that the following operations are done automatically when I open emacs. 

Finally, if there is any forum where is better for me to post my question, please tell me.
Thanks.


-----

I found another problem. If I run term on the right window, then I can't use Ctrl+x o to return the left window. I need to quit term then I can use Ctrl+x o. Is there anyway to return the left window without exit term?

I don't the "M-x shell" because it doestn't remember the commands I typed in the previous step.

---

