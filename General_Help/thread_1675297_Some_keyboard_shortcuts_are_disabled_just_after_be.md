---
title: "Some keyboard shortcuts are disabled just after being set"
date: 2011-01-25
forum: General Help
---

### Post by Mawh on 2011-01-25
Hi all,
I have a small problem on Ubuntu 10.10. I tried to set shortcuts to "show workspace 2" and "show workspace 2" (respectively to Alt+² and Alt=& (the two first keys on the numbers line on a french keyboard)), and they work fine until the next boot, where I find them disabled. They are still listed in the "keyboard shortcuts" app, but they don't work. If I re-assign them, they work until the next boot, etc.

Any clue ?

Thanks.

---

### Post by irv on 2011-01-25
To switch workspaces, why don't you just use the Ctrl/Alt arrow keys. They are set by default.

---

### Post by Mawh on 2011-01-26
Thank you Irv, these keys do work. But I was interested in needing only one hand to navigate between all my workspaces and open applications ; therefore, Alt+Tab and Alt+A/Alt+Z seemed perfectly suitable.

So, any idea why it doesn't work ? (it didn't in 10.04 either)

---

### Post by irv on 2011-01-26
I see the Alt+Tab is assigned to "Move between windows, using a popup window." Just to see if Alt+A and Alt+Z worked I tried it and it worked for me. So I don't know why it doesn't work for you. You are changing it in the System> Preferences> Keyboard Shortcuts aren't you?

---

### Post by Mawh on 2011-01-26
Yes they do work immediately after being set, but not anymore after a reboot. Yes, I set them in "keyboard shortcuts".

I may add that I'm using a Samsung N210 with a custom package that make the function keys work properly (voria ppa) - though I don't think that does interfere.

---

### Post by irv on 2011-01-26
> **Mawh said:**
> Yes they do work immediately after being set, but not anymore after a reboot. Yes, I set them in "keyboard shortcuts".

I may add that I'm using a Samsung N210 with a custom package that make the function keys work properly (voria ppa) - though I don't think that does interfere.

I guess the next question I would have is, After reboot and going back into keyboard shortcuts are they changed back to default setting? If so there might be a bug in the keyboard shortcuts. I didn't try this on my system. When I have time later I will give it a try.

---

### Post by irv on 2011-01-26
OK, I gave it a try. I set the shortcuts, rebooted, and they stayed. Look like everything is working like it should.
[ATTACH]182010[/ATTACH]

---

### Post by Mawh on 2011-01-27
Yes they are still set in "keyboard shortcuts" ; they just don't work anymore. I think it was already happening when I had freshly installed Ubuntu.

---

### Post by irv on 2011-01-27
> **Mawh said:**
> Yes they are still set in "keyboard shortcuts" ; they just don't work anymore. I think it was already happening when I had freshly installed Ubuntu.

I see I am running the same version as you, 10.10 but you could have different things and different settings that might be causing this for you. This might be a hard one to fix. It might even be a hardware difference. I wish I had a better answer for you but I don't. If someone else has an idea feel free to jump in.
Just for the record I check my keyboard model setting and it is "Generic 105-key (Intl)PC.

---

### Post by Mawh on 2011-01-29
I have the same keyboard layout... default one, I guess.

But as written earlier, this problem already happened with a freshly installed Ubuntu, so I'm inclined to think this is a hardware issue. Thanks for your help though.

(meanwhile, alt+arrows works fine, so I'm going to keep it ; thx !)

---

