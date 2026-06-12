---
title: "eclipse error at startup"
date: 2010-02-25
forum: General Help
---

### Post by erjoalgo on 2010-02-25
I was able to use eclipse an hour ago. Now, after booting back to Ubuntu from Windows, I get the following error when attempting to start eclipse:

An error has occurred. See the log file
/xx/xx/xx/.metadata/.log.

The xx are irrelevant directory paths.

I use eclipse heavily and without it, I cannot use Ubuntu. Please help.

---

### Post by erjoalgo on 2010-02-25
Solved my own problem. For anyone who might run into this, the error seemed to be related to the workspace, so I simply deleted the .metadata folder (hidden), and created workspace again. You can then do "import existing projects" from your old workspace.

---

