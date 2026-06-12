---
title: "gnome-do default terminal"
date: 2010-09-17
forum: General Help
---

### Post by jsvaughan on 2010-09-17
Hello,

(If there is somewhere more appropriate to post this question, my apologies! Please let me know where to)

In gnome-do I would like the gnome terminal to appear as a result of the terminal 'command' (i.e the Gnome Terminal plugin) but instead I get the xfce terminal.

I assumed this was because xfce was the default (as I am running an xfce session) but when I checked by:

sudo update-alternatives --config x-terminal-emulator

I find that the Gnome term is the default too.  

  Selection    Path                             Priority   Status
------------------------------------------------------------
* 0            /usr/bin/gnome-terminal.wrapper   40        auto mode
  1            /usr/bin/gnome-terminal.wrapper   40        manual mode
  2            /usr/bin/koi8rxterm               20        manual mode
  3            /usr/bin/lxterm                   30        manual mode
  4            /usr/bin/uxterm                   20        manual mode
  5            /usr/bin/xfce4-terminal.wrapper   40        manual mode
  6            /usr/bin/xterm                    20        manual mode

So is there a way I can change it please?  

Thanks for any help!

Jon

---

### Post by jsvaughan on 2010-09-18
I didn't see if before - there is a gnome-do forum so I have posted this question here instead.

[https://answers.launchpad.net/do/+question/125900](https://answers.launchpad.net/do/+question/125900)

---

