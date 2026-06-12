---
title: "smplayer keeps starting on different desktop"
date: 2010-06-08
forum: General Help
---

### Post by chriskin on 2010-06-08
well , just that
i don't know what might be the problem but smplayer keeps starting on the second desktop
no other application has shown this behavior yet but i don't know if this is just because i haven't used one that will or if it is just smplayer

---

### Post by yetiman64 on 2010-06-08
> **chriskin said:**
> well , just that
i don't know what might be the problem but smplayer keeps starting on the second desktop
no other application has shown this behavior yet but i don't know if this is just because i haven't used one that will or if it is just smplayer

In the interface tab in smplayer's preferences, try deticking "Remember position and size", move to desktop1 and close, then try and reopen it and see if it makes a difference. 

Or it could be you have an entry in the Place Windows feature of compiz for smplayer that could cause this style of effect (have used that feature on older Ubuntus for placing firefox on a particular desktop every time I opened it -sounds similar to what's happening here with your smplayer). 
If you have ccsm installed look in Place Windows > Fixed Window Placement > Windows with fixed viewport for an entry for smplayer and delete it.

---

### Post by chriskin on 2010-06-08
i tried deticking what you said but nothing changed
also, there is no entry where you said

-----
by the way i found that smplayer starts normally when i just open it (no video i mean) but goes to the other desktop when i start it with double clicking a video

---

### Post by chriskin on 2010-06-10
ok... i just tried some more videos and i found out the most strange thing : smplayer goes to desktop 2 only on HD videos (!)

edit 1:i will try reinstalling it
edit 2:nope, reinstalling didn't change anything

---

### Post by rvm4000 on 2010-06-10
That's really strange.

Try to delete the smplayer configuration (~/.config/smplayer/)

---

### Post by chriskin on 2010-06-10
> **rvm4000 said:**
> That's really strange.

Try to delete the smplayer configuration (~/.config/smplayer/)

it seems that it stays now 
Thank you  :D

but this seems too strange : i have already uninstall smplayer with "complete removal", wouldn't that solve the problem?

i mean, complete removal removes the configuration, doesn't it? :confused:

---

### Post by rvm4000 on 2010-06-11
No, removing an application doesn't remove the configuration stored on your home directory.

---

