---
title: "fork: Resource temporarily unavailable"
date: 2009-10-19
forum: General Help
---

### Post by Quantum7 on 2009-10-19
I thought I'd share the cause for this frustrating and perplexing message.

I had a fresh install of Jaunty and I noticed that soon after startup I would start to get this message when I tried to run any commands:
```
bash: fork: Resource temporarily unavailable
```I finally discovered that this process comes from having too many processes, yet I knew that I had only a few hundred processes running on my whole machine. Finally I figured out that I'd been lazy and used a .bashrc from a server which included the line
```
ulimit -Su 64
```This command keeps bash from spawning more than 64 processes. That's reasonable on a server, where I log in and usually will only run 1-2 processes at a time. But it's terrible on a desktop machine which runs bash as the login shell. Gnome used up about 50 processes, so after starting a few apps I quickly hit the limit.

Moral: Don't blindly reuse configuration files on widely different machines.

---

