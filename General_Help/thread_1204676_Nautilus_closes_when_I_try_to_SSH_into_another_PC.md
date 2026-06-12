---
title: "Nautilus closes when I try to SSH into another PC"
date: 2009-07-05
forum: General Help
---

### Post by xjgnsdof on 2009-07-05
I run 32-bit Jaunty and can't seem to SSH into another PC except from the command line. If I try to SSH into another PC through Nautilus (i.e., the "Connect to server..." option), my Nautilus window closes when I click on the SSH host machine that appears in the Places menu.

I tried running Nautilus from the command line to see the error messages, and all that appears after Nautilus closes is "Segmentation fault."

Why can't I SSH through Nautilus without the window closing?

---

### Post by iponeverything on 2009-07-05
> **elgilicious said:**
> I run 32-bit Jaunty and can't seem to SSH into another PC except from the command line. If I try to SSH into another PC through Nautilus (i.e., the "Connect to server..." option), my Nautilus window closes when I click on the SSH host machine that appears in the Places menu.


Is the connect to server option different in Jaunty? I have attached sreenshot of from Ibex. Because it does not have list of servers to click on.

> 
I tried running Nautilus from the command line to see the error messages, and all that appears after Nautilus closes is "Segmentation fault."


A segfault is caused by a bug in the code, it's sort of the real world equivalent of an elevator door opening and stepping into an empty shaft.

If you can easily reproduce the bug, open a report on launchpad.

---

### Post by xjgnsdof on 2009-07-05
"Connect to Server..." is an option in the "File" menu in Nautilus. It looks exactly the same.

I've used Ubuntu on this laptop for several months, installing and removing distros out of curiosity. I have never had this happen before.

Edit: When I click the "Computer" icon in Nautilus, the window closes suddenly as well.

---

### Post by xjgnsdof on 2009-07-05
OK, this is ridiculous. Now my other PC, running 64-bit Jaunty, doesn't let me SSH into other machines through Nautilus' "Places" menu/sidebar. This came out of nowhere, as it was working just fine earlier today. I didn't update any files, and I didn't reboot. It literally decided to stop working. Huh?

---

### Post by xjgnsdof on 2009-07-11
up

---

### Post by XCan on 2009-07-11
This is not a solution to your problem, but have you considered to use sshfs to mount the remote host's drive instead of the built in buggy features in Nautilus?

---

### Post by nemti on 2009-07-12
I am having exactly the same problem as you - both SSH and and the Computer icon cause a Segmentation Fault. Please open a bug report on launchpad (or I can do it if you like).

---

