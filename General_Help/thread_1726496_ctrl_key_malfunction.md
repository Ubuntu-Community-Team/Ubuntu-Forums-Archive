---
title: "ctrl key malfunction"
date: 2011-04-11
forum: General Help
---

### Post by vlf0lh41 on 2011-04-11
**Edit:** A simple reboot solved the problem! 

Hy!
My left control key has just stopped working on my laptop.
When I run 
```
xbindkeys -mk
```and press the left control key, I get the following: 

"NoCommand"
    m:0x10 + c:165
    Mod2 + XF86MyComputer

And I tried keymapping c:126 to Control_L with xmodmap which gave me mixed results: the ctrl key still did not function, but  when it gave me this result with xbinkeys -mk:

"NoCommand"
    m:0x10 + c:165
    Mod2 + Control_L

Any help is wellcome!
Thank you

---

