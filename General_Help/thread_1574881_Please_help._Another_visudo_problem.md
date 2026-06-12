---
title: "Please help. Another visudo problem"
date: 2010-09-14
forum: General Help
---

### Post by juil on 2010-09-14
I need major help guys.

I was following the documentation for Sudoer here:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

I executed 'sudo -E visudo'
Then i tried putting in 'Defaults    editor=/usr/bin/nano'

but instead I deleted a line. Out of panic I pressed some button and deleted another line. Then still in panic i closed the terminal in hopes that it didn't save what i did.

When I did 'sudo -E visudo' in the terminal again, it gave me the below error. 

```
E325: ATTENTION
Found a swap file by the name "/etc/.sudoers.tmp.swp"
          owned by: root   dated: Tue Sep 14 21:51:08 2010
         file name: /etc/sudoers.tmp
          modified: YES
         user name: root   host name: skynet-desktop
        process ID: 2553
While opening file "/etc/sudoers.tmp"
             dated: Tue Sep 14 22:08:02 2010
      NEWER than swap file!

(1) Another program may be editing the same file.
    If this is the case, be careful not to end up with two
    different instances of the same file when making changes.
    Quit, or continue with caution.

(2) An edit session for this file crashed.
    If this is the case, use ":recover" or "vim -r /etc/sudoers.tmp"
    to recover the changes (see ":help recovery").
    If you did this already, delete the swap file "/etc/.sudoers.tmp.swp"
    to avoid this message.

Swap file "/etc/.sudoers.tmp.swp" already exists!
[O]pen Read-Only, (E)dit anyway, (R)ecover, (D)elete it, (Q)uit, (A)bort:
```

I Recovered it. and it looks like the picture 'sudoevisudo.png'

Unable to edit it, i tried sudo visudo, but somehow it looks like it's FIXED as shown in 'SudoVisudo.png'! Why is this?? And can someone help me solve this problem?

---

