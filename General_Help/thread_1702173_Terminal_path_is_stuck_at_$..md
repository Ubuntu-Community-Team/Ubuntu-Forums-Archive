---
title: "Terminal path is stuck at $."
date: 2011-03-07
forum: General Help
---

### Post by Roasted on 2011-03-07
Long story short - I'm running Ubuntu on a Windows domain, and I was trying to automate a link being created on the desktop so users had a direct link to their folder on the Windows file server.

I ran:

gvfs-mount smb://fileserver/users/$()

This changed my prompt to $. I have no idea how to change it back. The funny part is, if I log into a completely different Ubuntu system on our Windows domain, my account still has $ in the terminal.

How do I change it back?

---

### Post by Habitual on 2011-03-07
close and restart terminal?

---

### Post by TeoBigusGeekus on 2011-03-07
Try
```
reset
```

---

### Post by wojox on 2011-03-07
You're .bashrc file appears to be messed up. What does this say:

```
echo $PS1
```

---

### Post by Roasted on 2011-03-07
None of the above worked. A user in the IRC channel helped me narrow it down. Basically, I need to set the default shell to /bin/sh by running "chsh" in terminal.

Problem is, I get an error that my user does not exist in /etc/passwd. Mind you, this is a domain account on the Windows domain.

If this were a local user, we'd be done. But I need to figure out how to change the default shell on domain users within Ubuntu.

Any insight?

---

