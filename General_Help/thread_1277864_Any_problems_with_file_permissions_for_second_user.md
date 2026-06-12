---
title: "Any problems with file permissions for second user?"
date: 2009-09-28
forum: General Help
---

### Post by Irihapeti on 2009-09-28
I am lending my EeePC with Hardy on it to my son for a trip. I've set him up as a second user, tested everything, and then removed my own account. (I backed the whole system up first.)

Everything seems to be working well, but I'm just wondering if there might be any file permission problems because his user ID is 1001 instead of the normal 1000. I'm mainly concerned about files downloaded or copied from other systems (such as his home PC) where the user ID is 1000.

Multi-user boxes seem to be common enough, so maybe some kind person can enlighten me here.

Thanks
Irihapeti

---

### Post by mang_ucup on 2009-09-28
That wouldn't be a problem i think, as your son only need to write to his personal folder (ussually under /home) but to do an system update or installation, you need to give your son admin rights and change /etc/sudoers to allow your son account to do sudo

---

### Post by Irihapeti on 2009-09-28
Thanks for your reply.

I made my son an administrator, and tested the account out before I deleted my own. (In fact, I deleted my own account from his one.) I ran sudo apt-get update, sudo apt-get upgrade and stuff like that with no problems.

He's OK about doing basic admin stuff in the terminal, such as chown, if anything untoward happens. And he can always send me an email :)

He's going to be testing it out before he leaves, so we have a little time to iron out any bugs.

---

### Post by 3rdalbum on 2009-09-28
Linux has always been designed as a multi-user system, and there's proper seperation between user accounts; so I'd be surprised if there were any problems.

The absense of UID 1000 shouldn't break anything.

---

