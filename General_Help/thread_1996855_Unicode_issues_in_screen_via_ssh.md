---
title: "Unicode issues in screen via ssh"
date: 2012-06-04
forum: General Help
---

### Post by Svip on 2012-06-04
I keep an irssi session in a screen on a server, which I ssh into from my machines.

But on my new laptop running 12.04, when I log in and attach my screen, all special characters appear as UTF-8 errors (a question mark in a square).  But it is not an issue with my terminal, because it handles UTF-8 find in other instances, furthermore, it handles UTF-8 when I am not using irssi through screen over SSH.

I can write with UTF-8 characters in nano on my server, if I want to, without errors.

And what weirds me out, is that it is only a problem when I connect *from this machine*, my other machines (along with guest machines I use here and there) **never** have this issue.

---

### Post by Svip on 2012-06-11
Well, it seems to be an issue that stems from 11.10, which persists when upgraded.  But re-installing 12.04 removes it.  Annoyingly, I don't really have that option.  So I wonder if it is possible to tell the system to re-install all packages.  Or at least whatever packages that might be related to this issue.

---

