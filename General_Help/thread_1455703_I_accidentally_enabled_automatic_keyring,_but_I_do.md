---
title: "I accidentally enabled automatic keyring, but I don't know how :S"
date: 2010-04-16
forum: General Help
---

### Post by carn1x on 2010-04-16
Ok, I've just installed 9.10 on 2 different systems for the first time, and I tried on System1 to do the libpam-keyring maneuvre to autoauth the keyring. 

This method failed and refused to authenticate even my login. I fixed this by reverting the gdm file back to it's original state from recovery console. 

Then, at some point soon after, at the keyring prompt, I was presented with a checkbox asking me if I'd like to automatically enter the keyring, which I checked, and from that point on it's not asked for my keyring password since.

I thought I would attempt to do this on system2, however libpam-keyring is already installed, and the only other change i made to system1 was the gdm file which has since been reverted. Also, both systems and their keyrings all share the same keyring password.

Am I missing something right under my nose? o_0 curious that I discovered that checkbox on system1, yet it doesn't appear to be googleable as to how to get it to appear.

Any advice please :) thanks

---

