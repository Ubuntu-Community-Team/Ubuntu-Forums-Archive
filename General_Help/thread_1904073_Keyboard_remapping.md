---
title: "Keyboard remapping"
date: 2012-01-04
forum: General Help
---

### Post by M80 on 2012-01-04
I am running Ubuntu 11.10 on a Dell Latitude D620.  

Currently my keyboard is not functioning properly.  The "p" key won't respond when pressed, but sometimes types by itself.  I need a way of disabling the key and then remapping the "p" to a different key.  I suppose there should be an easy way of doing this in the Terminal.

---

### Post by 1clue on 2012-01-04
The old school way to deal with that sort of thing is to use xmodmap.  Maybe it's still that way, I haven't looked for a long time.

---

### Post by M80 on 2012-01-04
> **1clue said:**
> The old school way to deal with that sort of thing is to use xmodmap.  Maybe it's still that way, I haven't looked for a long time.

Thanks, this works but with a caveat.  I typed:

```
xmodmap -e 'keycode 33='
xmodmap -e 'keycode 112=p P'

```

Which works until the computer is shut off.  After that, the changes disappear and I need to enter them again.  Any way to save changes permanently?

---

### Post by 1clue on 2012-01-04
Yes.  One way is to save those commands in /home/you/.xmodmap.

There's also a global file for all users, but I can't recall where it is.

---

### Post by M80 on 2012-01-04
> **1clue said:**
> Yes.  One way is to save those commands in /home/you/.xmodmap.

There's also a global file for all users, but I can't recall where it is.
Can you explain how to do this?  I'm kind of new to Linux.

---

### Post by 1clue on 2012-01-04
In your $HOME directory, create a file named **.xmodmap** (including the .) and copy the commands you quoted above into that file, and save it.  Done.

Log out, and log back in, and make sure it works for you.

If your account is the only one, then you're done.

---

