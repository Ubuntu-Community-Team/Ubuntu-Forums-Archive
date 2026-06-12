---
title: "LTSP server issues"
date: 2011-06-15
forum: General Help
---

### Post by nagylzs on 2011-06-15
We have two application servers in the office. Both of them had Ubuntu 9.04 Jaunty amd64 installed. Hw config: Intel i7 processor and 8/12 GB memory. They are used as LTSP servers. About 10-15 diskless clients connected to both.

We did not upgrade them since a year because they were actively used 16 hours a day. They were stable with some exceptions. Firefox+Flash caused X crash - so we disabled flashplayer. Also sometimes skype was hanging, or allocation 3GB+ memory, but that only happened rarely. Otherwise there were no problems with the system.

Since 9.04 is not supported, and we had some compatibility issues, we have upgraded these servers to 11.04. We used two different methods:

- for appserver1, we re-installed 11.04 over the existing installation and re-created the user accounts
- for appserver2, we upgraded to 9.10, then to 10.04, then to 11.04.

LTSP client images were recreated from scratch.

Here comes the problem. Since we upgraded them, the thin clients are crashing in various ways:

- complete freeze
- mouse disappears
- user is thrown out to login screen
- sudden reboot (although I have only seen this once)

For some users, it happens in every 5-15 minutes! For others, it happens one or two times a day. I can see nothing in the X session logs. 

We already removed skype, so we are not using any third party packages. Just firefox, thunderbird, LibreOffice, and some other native programs.

I was trying to determine what program is causing this, but I could not. Sometimes they crash after the user left her desk...

Clients are P3 and P4 Compaq machines. I also tried to use different computers but they also do the same thing.


Any suggestions?

Thanks,

  Laszlo

---

