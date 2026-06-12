---
title: "Switching Shells - question"
date: 2011-01-31
forum: General Help
---

### Post by SCMoney360 on 2011-01-31
I am taking a stab at switching to ksh and trying to learn some things, but am stuck at this one point.

I don't know what ksh is reading to get my settings.

I just want to make some changes, like the prompt, I keep seeing things like look in .profile and .kshrc, but my .profile never looks close to any examples I see and I don't even have .kshrc.

Any suggestions?  or steps I missed?

---

### Post by Brandon Williams on 2011-02-03
On an Ubuntu system, there is bash-specific processing in /etc/profile and the default ~/.profile, but there is no special processing for ksh in either of those files. Also, there is no default ~/.kshrc, though there is an example file that you could use as a base: /usr/share/doc/ksh/example.kshrc. You might want to copy that file over to ~/.kshrc to start with. If it doesn't look like your ~/.kshrc file is being sourced when you launch ksh, you might need to add code to your ~/.profile to make this happen. I'm not certain exactly what to do there, since it's been a while since I used ksh myself.

---

### Post by SCMoney360 on 2011-02-03
yep, worked like a charm...now to get to breaking .kshrc file.  Thank you greatly.

---

