---
title: "Pidgin with wvdial"
date: 2010-04-12
forum: General Help
---

### Post by ankit.vader on 2010-04-12
i use wvdial for internet access. But pidgin does not work in that. Is there anyway i can use pidgin while using wvdial?

---

### Post by gordintoronto on 2010-04-12
What makes you think Pidgin is not working?

---

### Post by ankit.vader on 2010-04-12
Its not connecting. Empathy works fine with wvdial, but i like using pidgin

---

### Post by equusaustralus on 2010-06-18
Not sure why it says that this thread is solved, but I found a solution from this post on launchpad: 

[https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/200047/comments/11](https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/200047/comments/11)
[INDENT]
There is a way, but it has become harder with every release.

- Intrepid: enter something in the "away cause" field, pidgin will
  connect
- Jaunty: stop NetworkManager while pidgin is running
- Karmic: /sbin/stop network-manager before pidgin is started[/INDENT]

"sudo /sbin/stop network-manager" worked like a charm on Lucid! ;)

---

### Post by ankit.vader on 2010-06-20
> Not sure why it says that this thread is solved, but I found a solution  from this post on launchpad: 

[https://bugs.launchpad.net/ubuntu/+s...47/comments/11]("https://bugs.launchpad.net/ubuntu/+source/pidgin/+bug/200047/comments/11")[INDENT]
There is a way, but it has become harder with every release.

- Intrepid: enter something in the "away cause" field, pidgin will
  connect
- Jaunty: stop NetworkManager while pidgin is running
- Karmic: /sbin/stop network-manager before pidgin is started[/INDENT]"sudo  /sbin/stop network-manager" worked like a charm on Lucid! :wink:

this works for me
```
pidgin -f
```

---

