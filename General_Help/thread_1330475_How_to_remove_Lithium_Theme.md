---
title: "How to remove Lithium Theme"
date: 2009-11-18
forum: General Help
---

### Post by giyad on 2009-11-18
Ok, I installed the Lithium theme properly but it never showed up in my list of themes.  When I hit customize, everything was in there, so I was using it and everything was great.  But, theres a problem with the firefox nav tab showing up black on black so I'm supposed to edit a file in the gtk, but I can't find it!!

When I go to /usr/share/themes there is nothing in there corresponding to Lithium!  So i deleted the panel and window themes individually and tried to reinstall it but now it won't work because it says it can't move over another directory....

What do I do?

---

### Post by fooman on 2009-11-18
try this:

open your home folder (places > home folder)...in the toolbar,  click view and put a check next to "show hidden files"

scroll down and find the .icons folder....look in there and see if you see a folder named "lithium" or similar.  right-click on the lithium folder and delete/move to trash.

then go back and see if you can reinstall it.

hope that helps.

---

### Post by giyad on 2009-11-18
> **fooman said:**
> try this:

open your home folder (places > home folder)...in the toolbar,  click view and put a check next to "show hidden files"

scroll down and find the .icons folder....look in there and see if you see a folder named "lithium" or similar.  right-click on the lithium folder and delete/move to trash.

then go back and see if you can reinstall it.

hope that helps.
Thanks man, it wasn't in .icons it was in .themes :-)

but it worked, and what I did to solve it from not showing up in the themes list was I just selected "Save" and created a Lithium entry... although if i delete that it won't delete the whole theme so I think I would still need to do what I did in the previous step to completely remove it.

---

### Post by fooman on 2009-11-18
> **giyad said:**
> Thanks man, it wasn't in .icons it was in .themes :-)



oops!  yeah,   ...i should have known that.  i had a similar issue with a mouse theme when i recently installed karmic.  the *mouse* theme was in .icons,  thus my confusion.

glad you got it sorted.  :D

---

