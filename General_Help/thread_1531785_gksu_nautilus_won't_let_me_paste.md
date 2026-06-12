---
title: "gksu nautilus won't let me paste"
date: 2010-07-15
forum: General Help
---

### Post by Macintoshkid on 2010-07-15
Hey I'm trying to copy some stuff from my old Mac hard drive but Mac has restrictions so I used gksu nautilus to access them and it works fine but when i right click and select copy I go to paste it and paste is greyed out. This happened to me like 3 days ago literally but I forgot how i got around it >.< BTW I'm using the live cd.

Thanks for any help!

---

### Post by ajgreeny on 2010-07-15
Why copy/paste and not just drag and drop in **gksudo nautilus**?

---

### Post by mcduck on 2010-07-15
Both the window where you copy from, and the window where you copy to, must be running as root. So you can't, for example, copy things directly from user's desktop to nautilus running as root. If you tried that, you'd copy as the normal user and then try to paste as different user, root...

So if you want to copy from one file manager window to another, then run "gksudo nautilus" to open the first window and then use the "New Window"-option from the File menu to open another one. Then you should be able to copy&paste between those windows.

..of course copy&paste inside the same file manager window, running as root, should work just fine. So if that's what you tried to do then there really is some problem other than just a confusion between the different user accounts.

---

### Post by Macintoshkid on 2010-07-15
Let me try drag n' drop. But both windows were gksu nautilus as root. In fact, i tried same window and two windows.

---

### Post by Macintoshkid on 2010-07-15
Drag and Drop does not work it said "The destination is read-only" Even when I know both windows were root.

---

### Post by Macintoshkid on 2010-07-15
Bump help. Plz

---

### Post by mc4man on 2010-07-15
Where are you trying to copy the files to? (assuming using livecd

---

### Post by prodigy_ on 2010-07-15
There's no magic to sudo (or gksu for that matter). It won't override filesystem restrictions for example. So the question is: are you sure that the destination **doesn't** reside on a read-only filesystem (a CD, a write-protected USB-stick, a partition mounted with 'ro' option, etc.)?

---

### Post by Macintoshkid on 2010-07-15
Well the thing is that the exact same thing happened a few days ago and i figured it out but now I forgot how. I'm copying from external to internal. I know I can I just forgot how. This is strange.

---

### Post by mc4man on 2010-07-16
> I'm copying from external to internal.

Still don't know what the internal partition 'is' - what filesystem, Os,?

Do you have ubuntu install on this pc?

whether or not I'd boot to the livecd then, System - Admin - Users and create a new user with the exact same username that has write permission on the internal partition.

Then log out and in as that user, mount the partition, if prompted for a password use the enter key <no password>

I would copy to that partition as the user, not root

---

