---
title: "Newbie's day-3 question - gnu emacs"
date: 2012-01-13
forum: General Help
---

### Post by chenxinghao on 2012-01-13
A search for emacs in the Software Center generated two choices: The GNU Emacs editor (metapackage) and GNU Emacs 23. Any significant differences between the two from users' perspective?
 
If both are installed, would there be two emacs application (with different names) or rather one overwrites the other?
 
(I just want to understand what to expect before install.)

---

### Post by chenxinghao on 2012-01-13
Found a relevant note at:
 
[http://askubuntu.com/questions/88336/difference-between-emacs-metapackage-and-emacs](http://askubuntu.com/questions/88336/difference-between-emacs-metapackage-and-emacs)
 
Went into Software Center and installed GNU Emacs editor Metapackage) without a glitch; opened a Terminal window and typed:
 
apt-cache show emacs | grep depends
 
and got the exact same output in the terminal.
 
Went into the Dash home and checked the Installed section and found GNU Emacs 23.
 
In the same Terminal window, checked the installation with "man emacs" and "which emacs", both showed all proper information.

---

