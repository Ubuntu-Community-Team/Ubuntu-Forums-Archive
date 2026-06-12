---
title: "hplip and hptools not working, broken links Reinstall?"
date: 2011-08-10
forum: General Help
---

### Post by Francis4344 on 2011-08-10
Hello everyone.

I could not get my HP printer to work. So in a not so brilliant move, I have uninstalled hplip and hptool and reinstalled it.

Even tough the command line message is telling that it is installed, the HPtoolbox would not run (both from the command line or the menu).

Did some digging and found that all the HP related files in /usr/bin were all labelled <broken link>.

So, I deleted all these.

Before I tried to reinstall again, should I worry about all the leftover hplip files?

Thanks!

Francis

---

### Post by Francis4344 on 2011-08-12
I have reinstalled hplip and hplip-gui from the command line.

In both cases, I get the message that the latest versions are installed. However, clicking on the menu shortcut produces nothing.

Using the terminal, the command sudo hp-check produces the following message:

command not found.

Any idea?

By the way, after reinstalling, all the /usr/bin/hp---related files all show broken links.

---

