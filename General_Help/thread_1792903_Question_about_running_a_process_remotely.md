---
title: "Question about running a process remotely"
date: 2011-06-28
forum: General Help
---

### Post by wrybread on 2011-06-28
I'm trying to run a long running process remotely through SSH. And I need that process to continue running after I log off.

When I run it normally from SSH, the process exits when I close the SSH window. 

Thanks for any help.

---

### Post by Bachstelze on 2011-06-28
Run it in a screen or tmux window.

```
sudo apt-get install tmux
tmux
yourlongcommand

```

Then Ctrl+B D (that is, first Ctrl+B then D alone) to detach tmux. You can log out from the system, and tmux will still be running with our process in it. To reattach it

```
tmux attach
```

---

