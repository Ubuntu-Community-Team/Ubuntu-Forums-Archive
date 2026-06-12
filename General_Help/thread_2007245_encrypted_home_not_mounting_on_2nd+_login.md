---
title: "encrypted home not mounting on 2nd+ login"
date: 2012-06-20
forum: General Help
---

### Post by Redsandro on 2012-06-20
I am running Ubuntu 12.04 with Cinnamon, and ever since I have 12.04 I have this issue.

I can boot my laptop [SIZE="1"](Lenovo Thinkpad Edge bought specifically for Linux)[/SIZE] and login just fine. However, **when I log *out*, I cannot log back *in* anymore.** I see a flash of a black screen, and go back to the login screen.

This never has been too much trouble, but now that I need to do some switching between users, this get annoying really quick.

I have discovered that **my ecryptfs encrypted home cannot mount again after it has been unmounted from logging out.** When I open a separate TTY and log in, just so that the user is busy and home will not be unmounted, the problem 'goes away'.

Any clue as to what's the problem?

Just in case it is relevant, I have a Crucial SSD with EXT4 filesystems. /home is separate.

---

