---
title: "Add new printer disabled"
date: 2010-06-26
forum: General Help
---

### Post by morrisjones on 2010-06-26
I have a locally connected Epson R340 printer.  The Lucid docs suggest Administration>Printing, Server>New>Printer. But that option is disabled in the menu!  No one else seems to have that problem.

Any suggestions?

Mojo
--
Morris Jones
Monrovia, CA
[http://mojo.whiteoaks.com](http://mojo.whiteoaks.com)

---

### Post by Exp HP on 2010-06-26
Is the option enabled if you open it as root?

(in terminal)
```
sudo system-config-printer
```

---

### Post by morrisjones on 2010-06-26
Nope, that didn't make any difference. What I discovered is that I'd encountered the "runlevel unknown" bug from Upstart. Not having a printer was just one of the side effects.  Cron was also not running.

I forced a "telinit 2" which brought up all the dead processes, and a reboot came up clean as well.

The printer is found.

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

Mojo

---

### Post by winjeel on 2010-06-27
I've got a similar problem. My printer is no longer installed and can't connect. I've done nothing to the printer since installing a long, long time ago, and have printed with it many times. What happened? Some update go wrong?

---

### Post by katjah on 2010-07-08
"TELINIT 2" command did the trick for me too!  Thank you very much!

---

