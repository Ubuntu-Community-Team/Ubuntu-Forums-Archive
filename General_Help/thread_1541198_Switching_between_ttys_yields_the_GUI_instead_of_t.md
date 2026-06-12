---
title: "Switching between ttys yields the GUI instead of the CLI"
date: 2010-07-28
forum: General Help
---

### Post by Krugar on 2010-07-28
Hello all,

I'm not sure how this happened. But after installing 10.04 today I can no longer switch between terminals with CTRL+ALT+Fn and yield a terminal console. Instead I get the same GNOME screen from tty7 displayed at whatever resolution I have set for the console terminal.

**This only happens after starting X**.

I boot into tty1 by setting GRUB_CMDLINE_LINUX_DEFAULT="text" in /etc/default/grub. During the time I'm here all is fine. I can switch between terminals normally. But when I do *startx* and get into Gnome, I lose the ability to go back to tty1-6. As I said, when I do it, I now get the same display in tty7 shown at whatever resolution and bit depth of the console.

What do you suggest I do?

EDIT:
I'm running Ubuntu on the latest VirtualBox (3.2.6). But I find this may not probably be the reason. So I'm choosing to post to the Ubuntu forums first. After all, it was working just fine yesterday. Only today, on a fresh installation of Ubuntu, I started experiencing this problem.

---

