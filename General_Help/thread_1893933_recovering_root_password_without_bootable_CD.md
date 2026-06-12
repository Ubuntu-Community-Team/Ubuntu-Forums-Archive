---
title: "recovering root password without bootable CD?"
date: 2011-12-11
forum: General Help
---

### Post by bcrowell on 2011-12-11
My brother-in-law set up an ubuntu box for my mother-in-law and shipped it to her. The three of us all live in different states. Apparently he messed up and forgot to write down the root password that he set. I'm going to try to walk her through the steps of fixing the problem over the phone. She is not very computer-literate. Assuming that her user account does not have admin privileges, and assuming that she does not have a bootable CD, is there any way for us to fix this without having to mail her a bootable CD? 

I don't know if the machine has a CD burner. If it does, then I imagine that we could have her download an ISO and burn it.

---

### Post by CharlesA on 2011-12-11
Ubuntu doesn't have the root account enabled by default. Unless your brother-in-law enabled it himself, you would do normal admin tasks by typing in the user's password.

---

### Post by bcrowell on 2011-12-11
Thanks, CharlesA. Sorry, I'm getting this all second-hand from my in-laws, but what you said makes sense.

I guess the problem must be that she doesn't have admin privileges for her user account -- which probably raises the same issues.

I'll try to figure out more about her situation by talking on the phone with her.

---

### Post by CharlesA on 2011-12-11
That would be a bit of a problem. Without sudo access there isn't much you can do unless you boot into recovery mode by holding down shift while GRUB is loading.

Check this page out for more info:
[http://psychocats.net/ubuntu/resetpassword](http://psychocats.net/ubuntu/resetpassword)

---

