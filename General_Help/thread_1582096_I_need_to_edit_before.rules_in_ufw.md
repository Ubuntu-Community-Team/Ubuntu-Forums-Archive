---
title: "I need to edit before.rules in ufw"
date: 2010-09-26
forum: General Help
---

### Post by archer88 on 2010-09-26
:confused:I'm running into a problem with ufw when enabled and need to edit before.rules but i simply do not know how to safely do so.
This is a known issue [https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/289906](https://bugs.launchpad.net/ubuntu/+source/ufw/+bug/289906).

The problem for me is;i issue the command sudo vi /etc/ufw/before.rules and i get there,i use the arrow keys to get to this part to  replace "-m conntrack --ctstate" to "-m state --state" and i do not know how to execute this safely.I am using enter keys,delete keys and...well i'm confused as to how to do this!!

Also,how do i save it after changes are made?

Thank you in advance.

---

### Post by robsoles on 2010-09-26
Welcome to UF.

I used to use VI and I prefer nano much more these days. Take a look at [http://www.washington.edu/computing/unix/vi.html](http://www.washington.edu/computing/unix/vi.html) - I expect that should help.

---

### Post by archer88 on 2010-09-26
[FONT=Comic Sans MS]:P[/FONT] Your expectations were correct!!


Straightened it out with the quickness thank you so much robsoles!!

---

### Post by robsoles on 2010-09-26
very welcome.

please consider marking your thread as 'solved' using the 'thread tools' in red above.

---

