---
title: "Manual setup of QJackctl"
date: 2011-01-13
forum: General Help
---

### Post by pakito15191 on 2011-01-13
After some time trying to solve something I broke, I found out the solution of it.
If you have any problem with the script before/after shutdown that doesn't let you open QjackCtl, you should edit it manually.
So I was looking for where the setup files are, to look for it manually and change it, and I found out where, they were at:
~/.config/rnbc.org/QjackCtl.conf
Some people (other threats) says that rnbc.org vary from one computer to another, as it was shown differently in other posts. This way is how it appears in my Ubuntu 10.10.
To open and edit the text file from terminal, just write:
```
gedit ~/.config/*.org/QjackCtl.conf
```The bit you would want to edit is after the tag [Settings] or [Options], and the default options for startup and shutdown scripts are:
[HTML]
StartupScript=true
StartupScriptShell=artsshell -q terminate
PostStartupScript=false
PostStartupScriptShell=
ShutdownScript=false
ShutdownScriptShell=
PostShutdownScript=true
PostShutdownScriptShell=killall jackd[/HTML]
That's all, I hope it helps someone.

PS: Sorry for my poor English.

---

