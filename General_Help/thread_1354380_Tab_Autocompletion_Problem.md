---
title: "Tab Autocompletion Problem"
date: 2009-12-13
forum: General Help
---

### Post by HalfEmptyHero on 2009-12-13
The tab autocompletion has stopped working for me when using apt. It seems to still be working for everything else but even if I type in all but one letter of the package I want to install, it doesn't complete it or show any options. I'm using Kubuntu Karmic.

---

### Post by Sin@Sin-Sacrifice on 2009-12-13
There are too many results for apt. Press tab a second time and you'll see the list.

---

### Post by HalfEmptyHero on 2009-12-13
No, this is not the problem. I can type in sudo apt-get install gimp-ga, where gimp-gap would be the only result, and nothing comes up. No matter how many times I hit tab nothing comes up for any package.

---

### Post by 3Miro on 2009-12-13
> **HalfEmptyHero said:**
> No, this is not the problem. I can type in sudo apt-get install gimp-ga, where gimp-gap would be the only result, and nothing comes up. No matter how many times I hit tab nothing comes up for any package.

I don't think this has ever worked like that. Tab only finds files and/or programs, it doesn't check the database. If you have downloaded the file you can get it from tabbing if you are in the same folder, but not otherwise.

---

### Post by HalfEmptyHero on 2009-12-13
This has always worked, I am not sure why it's not working now but it certainly used to. Its not just with the actually package files, its any apt command as well. For example, apt-get in + tab should bring me apt-get install, however now it does nothing.

---

### Post by john newbuntu on 2009-12-14
In your home directory, edit a file called .bashrc.  If it does not exist, create one.  Append the following lines and save the file:

# enable programmable completion features
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

Now close the terminal and open another one.  Try your completion command. Also make sure that you have a file called /etc/bash_completion.

---

### Post by HalfEmptyHero on 2009-12-14
Yep, this fixed it. Thanks a lot.

---

### Post by SLamontagne on 2010-07-13
Sorry to revive an old thread, but since it was the first given by google when I did a search for this issue, I would like to add something for completeness of the solution.

The solution proposed is working perfectly but to be complete I would suggest to copy the .bashrc file from /etc/skel/ to your home folder when your .bashrc has been removed or is missing. This way you will also benefits from some alias and settings that you can then simply modify.

But yes, for the auto-completion the stated solution is all you need. 
(It is contained in the default /etc/skel/.bashrc)

---

### Post by Simian Man on 2010-07-13
Even better solution: use zsh instead of bash.

---

