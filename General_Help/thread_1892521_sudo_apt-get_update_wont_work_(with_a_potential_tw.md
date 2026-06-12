---
title: "sudo apt-get update wont work (with a potential twist?)"
date: 2011-12-08
forum: General Help
---

### Post by gjwebber on 2011-12-08
Hi all,

I can see this is a common problem, but have looked through all of the solutions and none work for me. There is also something strange going on that I can't explain. Here's where I am so far:

First of all, I am behind a proxy. I have set it up in network settings, and can connect to the net through firefox using the "Use system setting" proxy option. All seems good so far.

Now when I come to doing a sudo apt-get update it just sits at 0% waiting for headers. I tried the "export http_proxy=xxx" method, makes no difference at all. Next I added the --print-uris switch to see what apt-get is trying to access. The strange thing here is, I can open all of the listed files using firefox. I am not being denied access.

What is going on here, and how can I fix it?

Thanks for any help,
Gareth

---

