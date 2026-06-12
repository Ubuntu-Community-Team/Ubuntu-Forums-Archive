---
title: "acpi issues , any ideas ?"
date: 2006-03-13
forum: General Help
---

### Post by crxyem on 2006-03-13
ok I've got a dell inspiron 6000 using a wireless network conenction via ndiswrapper and wpa_supplicant, if I enable acpi for the lid switch and choose standy-by it works just fine. here's the issue at hand

I mount my samba shares w/ fstab, samba shares work wonderfully

now if I close the lid the system goes into stand-by which is great, the problem I loose my samba shares when I wake the system from stand-by. 

I have tried sudo mount -a with no luck , I can then remap my samba shares from a terminal. 

so any have any ideas how to correct this, as I don't want to have to teach my wife how to mount shares 

thanks in advance

---

### Post by mozetti on 2006-03-14
I'm new here & to Linux, but until you figure out the 100% fix, couldn't you just write a bash script, give it an icon, and put it on the desktop/bar? Then, she can just click it whenever the shares aren't available.

---

### Post by crxyem on 2006-03-14
I guess but, I'm trying to show her linux is extremely better than windows, and when it doesn't do something right she mocks me, so I need a propper solution.

---

### Post by mozetti on 2006-03-14
haha, ok. Like I said, I'm new but let me wing it until someone better comes along. Pardon my misuse of terminology, if it occurs.

Ok, you're mounting samba shares in fstab - so, during startup it mounts the shares for you at a certain run-level. It appears that this is a run-level that doesn't happen when the laptop "wakes up" from standby.

Can't you just snip the code that mounts the samba shares during startup and put it into the function that runs when you come out of standby? Would it be?:

```
mount -a
```

Thinking about it, I guess it isn't really "code" that runs during startup since it's using fstab. But, if you use the mount command I typed above, wouldn't this accomplish what you want? 

Or, if you didn't want to use that method, couldn't you just put code to re-mount the samba shares into the function used to bring the system out of standby?

---

### Post by crxyem on 2006-03-14
You know that's a great idea, i'll have to look into it.


anyone else have any other bright ideas ??

---

### Post by abalone on 2006-08-26
(edit: I would delete this if I could)

---

