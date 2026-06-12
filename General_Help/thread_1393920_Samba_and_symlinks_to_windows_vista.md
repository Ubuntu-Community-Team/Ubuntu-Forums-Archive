---
title: "Samba and symlinks to windows vista"
date: 2010-01-29
forum: General Help
---

### Post by jiggz88 on 2010-01-29
Recently upgraded from 9.04 to 9.10 and got slapped with a nice enjoyment of bugs that made me utterly regret upping the disto. After i quelled most of the issues, I seem to have found a new one thats got me just annoyed to all hell...samba no longer carring over symlinked folders for display in windows, specifically in my case, vista.

Tryed chmod, tried recreating the share, tried chown'ing again. No avail.

Suggestions? 


I'm not a simpleton so dont give me any of the crap like, "did you make sure you were sudo'd while you did the chown's?" So lay on the *nix thick and heavy so I can forget I still have to use windows everyday.

---

### Post by soylent_green_is_hamster on 2010-02-27
Yo,

did you get this fixed?

I'm an Arch Linux user, and I recently upgraded samba to 3.4.6-1, and symlinks aren't followed anymore.

Like you, I'm no simpleton, and I've tried all the usual stuff, including setting "follow symlinks = yes" in the smb.conf

This is a really annoying problem for me....is there a new option to set this or something??

---

### Post by soylent_green_is_hamster on 2010-02-28
managed to find a solution to this if anyone cares:

try setting "unix extensions no" in the global section of your smb.conf

I don't know exactly what that means, but it does the trick

---

