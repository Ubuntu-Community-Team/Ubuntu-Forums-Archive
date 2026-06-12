---
title: "Sudo permissions and timeouts"
date: 2010-02-03
forum: General Help
---

### Post by Muscovy on 2010-02-03
I want to make a script for something, but I'm worried the timeouts on sudo permissions (how you can't got more than 5/10 minutes between sudo commands before needing your password again). Basically, I don't want my script to be redundant and require overseeing for password inputs.
  Take this example:
```
sudo echo Hello.
sleep 6000
sudo echo This is text.
```
  This shows the basis of the problem. I will need to enter my password twice.
  Would allowing it to run uninterrupted be as easy as running this theoretical shell script his sudo to begin with?

---

### Post by jken146 on 2010-02-03
You want to do something like this:
```

sudo bash -c "echo foo ; sleep 5000 ; echo bar"

```

---

