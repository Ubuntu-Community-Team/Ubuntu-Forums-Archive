---
title: "Application Lauch Failure by Concurrent User in Common Gnome Session"
date: 2012-05-10
forum: General Help
---

### Post by gazza_11 on 2012-05-10
Ubuntu 11.04; 2.6.38-15-generic.

I was logged in to the Gnome desktop environment, version: 2.32.1; build date: 14/04/11, and, after a while, wanted to temporally concurrently browse the Web as a different user.  I opened up a graphical terminal and issued the following commands:

```
xhost SI:localuser:joe
gksu -u joe seamonkey
```

(Joe being the different user name -- example only.)  These successfully added this different user to the xhost localuser access control list, and started up Seamonkey web browser (version: 2.9.1), allowing its display in my logged-in desktop session.  A Web page I was viewing had a link to a PDF document which I wanted to see, so I clicked on it to open it in a new tab, which I switched to.  The browser started up Adobe Reader 9, version: 9.5.1; dated: 03/07/2012, for display within the browser's viewport, turning it dark (that's okay), but a dialogue box popped up with the following error:

'Could not launch Adobe Reader 9.5.1. Please make sure it exists in PATH variable in the environment. If the problem persists, please reinstall the application.'

I check the PATH environment variable and all was well.  However, I noticed something on in the graphical terminal, caused by the browser's invocation of Reader:

'Adobe Reader does not need to be run as a privileged user. Please remove 'sudo' from the beginning of the command.'

I can't see how to do the above request.

What can I do?

---

### Post by gazza_11 on 2012-05-26
This is a bug?

---

