---
title: "Error changing user full name"
date: 2010-10-04
forum: General Help
---

### Post by krige on 2010-10-04
Whenever I try to change a user full name, through System / Administration / Users and Groups, I get the following error:

The configuration could not be saved
An unknown error occurred.

Anybody know what could be the problem?

Running Ubuntu 10.04.1 LTS 64 bit, freshly installed.

---

### Post by philinux on 2010-10-04
> **krige said:**
> Whenever I try to change a user full name, through System / Administration / Users and Groups, I get the following error:

The configuration could not be saved
An unknown error occurred.

Anybody know what could be the problem?

Running Ubuntu 10.04.1 LTS 64 bit, freshly installed.

You cannot change your username while logged on.

[http://www.liberiangeek.net/2010/07/how-to-change-your-usernameuserid-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/how-to-change-your-usernameuserid-in-ubuntu-10-04-lucid-lynx/) Or

[http://ubuntuforums.org/showthread.php?t=821685](http://ubuntuforums.org/showthread.php?t=821685)

---

### Post by krige on 2010-10-04
> **philinux said:**
> You cannot change your username while logged on.

[http://www.liberiangeek.net/2010/07/how-to-change-your-usernameuserid-in-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/how-to-change-your-usernameuserid-in-ubuntu-10-04-lucid-lynx/) Or

[http://ubuntuforums.org/showthread.php?t=821685](http://ubuntuforums.org/showthread.php?t=821685)

That did the job, thanks a lot! :)

How about changing the error message to a more meaningful one like the following?

The configuration could not be saved:
You cannot change your username while logged on.

---

