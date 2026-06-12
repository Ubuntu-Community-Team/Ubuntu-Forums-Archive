---
title: "caps lock problem"
date: 2009-10-12
forum: General Help
---

### Post by cong06 on 2009-10-12
I'm having a problem with caps lock in ubuntu.

I found the article recommending "setxkbmap." ([http://www.filecluster.com/reviews/112008/how-to-fix-the-caps-lock-shift-control-problem-under-ubuntu/](http://www.filecluster.com/reviews/112008/how-to-fix-the-caps-lock-shift-control-problem-under-ubuntu/))
My problem is unusual because it seems that the capslock button is constantly being pushed, so setxkbmap didn't help much. If I run the command `xmodmap -e "clear Lock"` then it tells me to release the capslock button.

This isn't just a hardware problem, though, if I switch to another tty, the capslock problem goes away, and I can type lowercase without holding the shift button.

Are there any tricks I'm missing that would help get rid of capslock?

---

### Post by Giblet5 on 2009-10-12
Is this a laptop with an external dock/kbd?

USB kbd, or PS/2?

Did this start happening after you tried to remap the capslock key, or did you try to remap the capslock key because of problems?

---

### Post by mike555 on 2009-10-12
I use "Xkeycaps" ,from package manager , it lets me set any key to another ... I set my keylock to a shift key (without lock) ...........

---

### Post by cong06 on 2009-10-13
It's a laptop, but no dock, it's the original keyboard.
The problem started, so I started trying to fix it by using this, not the other way around.

One thing I did was use xmodmap, which I successfully used to to switch the keys (Caps lock and scroll lock), but apparently since Caps lock is already set, it doesn't un-toggle.

What's really frustrating is that it seems to be set in some sessions and not others. Often when I log into gdm, capslock isn't pressed, but then once I open up a terminal and really need normal lowercase letters, it strikes.

---

