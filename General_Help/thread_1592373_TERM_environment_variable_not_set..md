---
title: "TERM environment variable not set."
date: 2010-10-10
forum: General Help
---

### Post by XerXeX on 2010-10-10
Hi, 

I just upgraded to 10.10, I use Tilda (terminal client) on my desktop but now when I type "clear" it says "TERM environment variable not set." instead of clearing the screen. Also commands like "tree" does not show folders and files in color like they did before upgrading. Help is much appreciated. 

echo $TERM
dumb

?????

---

### Post by XerXeX on 2010-10-10
Found a workaround for the bug here for anyone with the same problem: [https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/635804](https://bugs.launchpad.net/ubuntu/+source/tilda/+bug/635804)

echo "export TERM=xterm" | sudo tee /etc/profile.d/set_term.sh && source /etc/profile

---

### Post by ninjapirate89 on 2010-10-11
Thank you for this, I was experiencing the same thing in guake.

---

### Post by RIchard James13 on 2010-10-12
I'm also having the exact same problem in xfce terminal. Was working in 10.04 now it doesn't in 10.10

I wonder what changed?

---

### Post by zathraszero on 2010-10-14
Wouldn't you want to set TERM to "xterm-color" and not just xterm?

---

