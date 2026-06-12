---
title: "Desktop files have disappeared"
date: 2009-11-15
forum: General Help
---

### Post by billynom8s on 2009-11-15
Running version 8.10

I have a strange problem with my desk top. My desk top is only showing the back ground picture that I have set. Any files, shortcuts etc that I know are there, don't appear. I can see that they are there by going to the terminal and using ls to list them. I can't see the files using Nautilus because when I click on desktop, Nautilus closes. I'm not sure when this started happening, so I can't really relate it to any event. I haven't changed any permissions for the desk top.

Has anyone seen this type of problem before? Any body know a fix?

:-(

---

### Post by arnab_das on 2009-11-15
press alt+F2

type "gconf-editor"

from there go to Apps>Nautilus>Desktop

now see if the "volumes visible" is unchecked. if unchecked, select it.

now check if ur icons have reappeared.

---

### Post by billynom8s on 2009-11-15
I did that and it was checked. The icons are still not there.

---

### Post by billynom8s on 2009-11-17
Any body else got any ideas? The problem is still there.

---

### Post by P4man on 2009-11-17
run```
 df -h 
```in a terminal and post the output. Im guessing your / partition is full?

---

### Post by billynom8s on 2009-11-17
I've upgraded to version 9.04 and that fixed it. I didn't read that last reply beforehand, so I don't know if was a fix or not.

Thanks

---

