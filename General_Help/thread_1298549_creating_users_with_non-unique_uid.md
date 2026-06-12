---
title: "creating users with non-unique uid"
date: 2009-10-22
forum: General Help
---

### Post by Nullexe on 2009-10-22
I'm having some problems with usermod and was wondering if anyone else seems to have this issue. 

I would like to create 12 accounts on a hardy system, each of the 12 accounts must have the same uid (1000) for RADIUS reasons.

The usermod man page shows that: 
```
sudo usermod -o -u <uid> LOGIN
```
should do the trick, unfortunately this prints out the usermod options and doesn't change the uid.

I know the account has sudo permissions, I also dropped to a root shell to test.  

Has anyone else ran into this before or have any ideas?

UPDATED: The order matters!!!
```
 usermod -u <uid> -o LOGIN 
```
works, the ordering of the flags matter in this case (though it doesn't seem to be documented)

---

### Post by undecim on 2009-10-22
Was there anything (i.e. an error) printed before the options?

---

### Post by Nullexe on 2009-10-23
nope, no errors messages.

---

