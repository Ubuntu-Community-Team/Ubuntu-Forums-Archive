---
title: "The dreaded number lock won't work question"
date: 2010-05-02
forum: General Help
---

### Post by winecurmudgeon on 2010-05-02
Number lock won't stay on or off. There doesn't seem to be any pattern. I'll be typing, and use the number keypad to move the cursor to the far left or right, and get a number instead. Or the opposite will happen.

I have tried ctrl-alt-numlock. I have tried installing numlockx. I have tried, in fact, every solution listed here that I can find. I had the same problem with 9.04, and found a terminal command (I think) that fixed it. But I didn't save the solution anywhere, and I can't find the post with that solution in the forums.

---

### Post by iponeverything on 2010-05-02
try a different keyboard, I think the one that your using has a short.

---

### Post by winecurmudgeon on 2010-05-02
I don't think that's it, since the number lock was working on the same keyboard with 9.04 before I did a clean install of 10.04 on Friday.

---

### Post by dino99 on 2010-05-02
into synaptic: numlockx

sudo dpkg-reconfigure numlockx

---

### Post by Pjotr123 on 2010-05-02
Did you automate numlockx?
[http://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-NumLock-turn-on-automatically](http://sites.google.com/site/easylinuxtipsproject/first#TOC-Make-NumLock-turn-on-automatically)

If that's not a solution, I think you could try physically cleaning your keyboard.

---

### Post by winecurmudgeon on 2010-05-02
Thanks for the thoughts. None of that has helped. Like I say, the crazy thing is that I didn't have this problem two days ago with 9.04. It started the second I did a clean install of 10.04.

I'm seriously thinking of buying a new keyboard.

---

### Post by dino99 on 2010-05-02
> **winecurmudgeon said:**
> Thanks for the thoughts. None of that has helped. Like I say, the crazy thing is that I didn't have this problem two days ago with 9.04. It started the second I did a clean install of 10.04.

I'm seriously thinking of buying a new keyboard.

then you may look at .xsession-errors and logs to find a way to debug

---

### Post by smokey_58au on 2010-05-02
Try the method in this link:

[http://ubuntuguide.net/enable-number-pad-numlock-at-startup-in-ubuntu-login-window](http://ubuntuguide.net/enable-number-pad-numlock-at-startup-in-ubuntu-login-window)

I have used this on my home PC and various laptops since 8.04 and it works every time.

---

