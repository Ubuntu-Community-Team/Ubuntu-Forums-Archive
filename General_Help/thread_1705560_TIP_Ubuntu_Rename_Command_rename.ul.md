---
title: "TIP Ubuntu Rename Command: rename.ul"
date: 2011-03-12
forum: General Help
---

### Post by NNisa on 2011-03-12
Hey guys,

This TIP goes to provide on future searches what is in fact a quite simple solution.

After reading some threads on this no one seems to provide a proper and clear answer to what users are looking for. 

The rename command in ubuntu is a Perl script that works differently than the rename linux utility. It provides in someways more flexibility but has no tab completion and requires some more typing. 

Answers most commonly defer people to attempt to write their on script or to use the mv command instead which does not work for multiple files nor provides the use of the rename command users are used to.




If Ubuntu users want to use the common linux rename command with tab completion they can call this simply by typing:

rename.ul 

(eg. rename.ul old new files)

instead. If you find yourself using it on a regular basis you can set an alias in your .bashrc file as so:

alias rename='rename.ul'

With this set you will be able to use the linux rename utility just as you are used to.



Hope you guys find this clarifying and useful. ;)



Cheers,

NNisa

---

