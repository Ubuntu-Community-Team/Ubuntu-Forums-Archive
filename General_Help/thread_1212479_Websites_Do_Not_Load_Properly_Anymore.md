---
title: "Websites Do Not Load Properly Anymore"
date: 2009-07-13
forum: General Help
---

### Post by jr_herman on 2009-07-13
Hello):P,

I recently ran into a glitch that I cant seem to fix or find solutions on the forums.

Websites similar to the link below will not load the pictures associated with each product. Other websites that generally give a preview of video clip before you click doesnt load those previews anymore either. The site worked the very first time I loaded it and now doesnt load anymore. 

Ideas???
](*,)

[http://www.bluefly.com/Acrobat-Men/_/N-1z140nwZ1aas/numPerPage-100/list.fly](http://www.bluefly.com/Acrobat-Men/_/N-1z140nwZ1aas/numPerPage-100/list.fly)

---

### Post by shane2peru on 2009-07-13
> **jr_herman said:**
> Hello):P,

I recently ran into a glitch that I cant seem to fix or find solutions on the forums.

Websites similar to the link below will not load the pictures associated with each product. Other websites that generally give a preview of video clip before you click doesnt load those previews anymore either. The site worked the very first time I loaded it and now doesnt load anymore. 

Ideas???
](*,)

[http://www.bluefly.com/Acrobat-Men/_/N-1z140nwZ1aas/numPerPage-100/list.fly](http://www.bluefly.com/Acrobat-Men/_/N-1z140nwZ1aas/numPerPage-100/list.fly)

Hmm, perhaps a flash issue?  I'm not 100% sure.  One thing you can do to test the problem is this, close firefox, then open a terminal   **Applications -> Accessories -> Terminal**  Then try this:
```

mv ~/.mozilla ~/.mozilla.bak

```
(This moves the whole mozilla profile folder to a different location, thus giving you a clean slate to work with).
Then re-open firefox (you will be back to a normal firefox thing all book marks are in the moved folder and don't appear.)  Open the site and see if that works for you.  

Shane
PS  it may be good to back up your bookmarks before you do this if you have a lot of them, if not this can be done later too.

---

### Post by jr_herman on 2009-07-18
Sorry,

But that didnt work either. And the bookmark thing did exactly what you said.

](*,)

---

### Post by y-lee on 2009-07-18
Hmm maybe you have the opton to load images turned off. You can try:

[LIST]
[*]Click on **Edit** in FF's menu, and select **Preferences**

[*]In the **Preferences** window, select the **Content** panel.

[*]Make sure there is a check mark next to **Load images automatically**

[*]Click on **Exceptions**... next to **Load images automatically** to open the *Exceptions - Images* window.

[*]In the *Exceptions - Images* window, look at the list of sites. Make sure the sites with which you're having trouble are not in the list.

[*]Close the *Exceptions - Images *window.

[*]Click OK to close the **Options** window

[*]Close the** Preferences** window
[/LIST]

---

### Post by jr_herman on 2009-07-19
Thanks. That did the trick. That site and others ended up on that exception list.

---

### Post by y-lee on 2009-07-19
> **jr_herman said:**
> Thanks. That did the trick. That site and others ended up on that exception list.

Great, i hoped that was it instead of some harder issue.

---

