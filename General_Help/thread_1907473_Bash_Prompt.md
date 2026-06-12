---
title: "Bash Prompt"
date: 2012-01-11
forum: General Help
---

### Post by lenwood on 2012-01-11
Hi All, I'm working on a remote Ubuntu server through the terminal on my Mac. Over the weekend I configured SSH keys to work, and somehow in the process I wiped out the settings for my Bash prompt. I lost color coding on files & folders, and I also lost command history via up/down arrows. Can someone point me in the right direction?

Thanks,
Chris

---

### Post by Lars Noodén on 2012-01-11
You can find the original .bashrc and .profile copies in the directory /etc/skel.   Copy from there and you'll restore the defaults.

---

### Post by jim_deadlock on 2012-01-11
FYI, your previous commands are stored in ~/.bash_history so if that's gone missing you'll just have to start fresh.

---

