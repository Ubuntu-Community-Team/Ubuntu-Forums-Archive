---
title: "No Users with sudo privileges"
date: 2010-04-15
forum: General Help
---

### Post by christguard on 2010-04-15
hi guys, so we are troubleshooting our way into linux freedom. But my bud and I just screwed up, false, I just screwed up. It would seem I got onto a tutorial with a typo. I was adding me and my bud to a new group I created, but I used -G instead of -g as the tutorial suggested, I think this removed me from all other groups and put me in the new one. The same with my bud. Now I dont have sudo privileges, nor does my bud, and we have not set a password for the root account. Is there hope?

Example
```
sudo ls -l
USER@SERVER:/var$ sudo password for USER:
USER is not in the sudoers file. this incident will be reported.
USER@SERVER:/var$

```

---

### Post by _0R10N on 2010-04-15
this might be a nonsense, but you could try to install ubuntu on other partition and then accessing to your /etc/passwd file and set your user with 0 as primary group...

---

### Post by bcbc on 2010-04-15
Boot into recovery mode - hold down shift when computer boots to the get grub menu (in karmic) or ESC (if before karmic) - and then drop to a root shell.

---

