---
title: "init help"
date: 2010-06-27
forum: General Help
---

### Post by flyingsliverfin on 2010-06-27
heres what ive done: i went to system monitor and killed nautilus. i want to start it up again without restarting (even though thats probably easier). i noticed that if i run 'nautilus' in the terminal, my folders on my desktop come back, but as soon as i close that nautilus the folders go again.

do i have to go through init?

if i do can some1 explain what init is, initrd (same thing?), how to use init for starting and stopping jobs etc.

thx

---

### Post by dabl on 2010-06-27
In your terminal, issue the command as 

```
nautilus &
```

Then you can close the terminal and the desktop will remain the same.

---

