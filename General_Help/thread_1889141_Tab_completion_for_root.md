---
title: "Tab completion for root"
date: 2011-11-30
forum: General Help
---

### Post by melipone on 2011-11-30
when I sudo to root on Ubuntu (lucid lynx), root does not have tab completion. I have uncommented out the lines below in /etc/bash.bashrc but it still does not work. Any ideas?

#if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
#    . /etc/bash_completion
#fi

---

### Post by oldos2er on 2011-11-30
Root's bashrc is in /root/.bashrc

---

### Post by mikejonesey on 2011-11-30
hmm, i though that both tab completion was default in bash and that root's shell was bash...

double check roots shell has not been changed from bash

---

