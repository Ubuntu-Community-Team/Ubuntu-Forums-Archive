---
title: "Password and Encryption Key chains"
date: 2009-06-29
forum: General Help
---

### Post by tthomas48 on 2009-06-29
So I've really been enjoying the "Passwords and Encryption Keys" feature that was introduced a few releases ago. I have an ssh key generated on my local machine that I've deployed to various machines, and I have a machine at my office that has an ssh key that has been deployed to various other machines. I use the work machine when I'm at home quite frequently for compiling and deploying code.

I'm wondering if there's an easy way to forward to a secondary ssh agent. I've tried to setup my bash profile to automatically load an ssh agent on first login to my work computer, and that works when I ssh in, but then when I login via the GUI using something like FreeNX, the agent no longer loads properly in gnome. 

Is there some simple way to tell the command line to use the GUI's agent and vice-versa. Sorry if I'm not describing the problem well.

---

