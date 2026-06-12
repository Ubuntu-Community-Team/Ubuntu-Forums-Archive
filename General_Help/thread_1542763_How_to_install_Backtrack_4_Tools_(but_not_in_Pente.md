---
title: "How to install Backtrack 4 Tools (but not in /Pentest directory)"
date: 2010-07-31
forum: General Help
---

### Post by freelancer i386 on 2010-07-31
Is there anyone who has figured out how to install penetration testing tools from Backtrack 4 (offensive-security) repository like all other programs (NOT IN /pentest DIRECTORY).

---

### Post by GrantStoner on 2010-09-12
Best bet is to add the repos (not the B|T repos, but the ones for the tools). If you use the B|T repos, there's chances it will mess things up terribly. The devs at B|T don't condone using their repos on Ubuntu installs because they use their own custom kernels, and custom gcc options. Also, B|T only has limited bandwith on their servers, and they don't want the TONS of Ubuntu users leeching off their server every time they do updates and whatnot. Most of them can be found in the Ubuntu repos anyway.

---

