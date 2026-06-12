---
title: "Desktop Icons Disappear"
date: 2009-07-13
forum: General Help
---

### Post by s1mp13m4n on 2009-07-13
Hello everyone.  I am using Ubuntu 9.04 with Gnome.  I have my computer set up so I can access three Windows XP machines i my house.  I gain access to their storage by clicking on Places, Network.  It has been working fine, but now when I do that my desktop icons go away.  The only way I can get them back is to log out and log back in.  What is going on, how do I fix this?

---

### Post by master_kernel on 2009-07-13
Nautilus is crashing for some reason. To find the problem, crash it, open a terminal and type 'nautilus', then crash it again. The answer will show in the terminal.

---

### Post by s1mp13m4n on 2009-07-13
Here is the result of what you asked me to do:

paul@paul-laptop:~$ nautilus
Initializing nautilus-dropbox 0.6.1
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:15290): WARNING **: Unable to add monitor: Not supported
Segmentation fault
paul@paul-laptop:~$ 

What is my next move?  :)

Update: When I load a terminal window and type nautilus my desktop icons re-appear, but when I close the terminal window they disappear again.  Does any of this help?

---

### Post by s1mp13m4n on 2009-07-13
Bump?  I am sorry about that...but this is very frustrating.  Thanks for the help in advance.

---

### Post by CatKiller on 2009-07-14
I'm afraid I know nothing about sharing with Samba, so I can't help you there.

> **s1mp13m4n said:**
> Update: When I load a terminal window and type nautilus my desktop icons re-appear, but when I close the terminal window they disappear again.

When you run Nautilus from the terminal, it starts again and is able to draw the background and icons as it should. But closing the terminal stops any programs that are running in the terminal. (This is true for all programs)

There are at least two ways round it, now that you've got the information about the crash that master_kernel was after. You can either background the nautilus process by running **nautilus &** or just start it again from the Alt-F2 Run dialogue. Either of these should stop nautilus being closed again when you close the terminal window.

---

### Post by master_kernel on 2009-07-14
You may be missing the samba package: [https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/211966](https://bugs.launchpad.net/ubuntu/+source/nautilus-share/+bug/211966)

---

