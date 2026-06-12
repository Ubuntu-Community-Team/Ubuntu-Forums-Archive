---
title: "Broken security settings"
date: 2010-07-27
forum: General Help
---

### Post by Gawayn on 2010-07-27
I'm an idiot.

I ran 
```
chmod o-rwx -R /
```

I've gotten ssh working for non-root users among many other things.
Right now I can't get samba to work again. The services list is completely disfunctional... I type service samb (then hit tab) and no autocomplete. I try service samba restart and it says samba is an unrecognized service.

I also can't use this tool for apache or any other service that actually exists on the box (and they're currently working). How can I get this service tool to work again?

Are there any other concerns I should have off the get-go? I imagine I'll be fixing this for a long time.

---

### Post by Bachstelze on 2010-07-27
You're pretty much toast, all you can do is reinstall.

---

### Post by Gawayn on 2010-07-27
Is there any super fancy command I could run to copy the permissions from another box with Ubuntu installed on it to this one? Anything? =(

---

### Post by dino99 on 2010-07-27
unique solution done with post #2 above :(

---

