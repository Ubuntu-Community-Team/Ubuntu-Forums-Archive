---
title: "Rebind space, caps, enter, backspace. A challenge indeed"
date: 2011-05-30
forum: General Help
---

### Post by Guntotingbastard on 2011-05-30
Completely new to Linux, I a few days ago installed Ubuntu 11.04. I've come to really like it and I've almost got it setup just as I want it. There is only one big thing.
I'm typing with a custom keyboard layout, and after asking google for help, I found out that I was supposed to edit  /usr/share/X11/xkb/symbols/se
So I did, all good. The custom layout is working!
Then I was going to customize it, and here is my problem. I have no idea how to do it. I found out how to rebind the "normal" buttons. But how to rebind Space, caps lock, enter and backspace I do not know.

What I wish to do is:
Caps Lock outputs Enter/Return.
Enter outputs Backspace.
Backspace outputs Caps Lock.

For reference, here is a bit of my keyboard-file:
key <AB10> { [ z,          Z,          guillemotleft,       none ] };
This is the bind for the button Z. First it says "key <AB10>, which is the buttons physical placement. This is where the problem lies. I do not know what space, caps... are named. (After that is the normal, unmodified key "z", then with shift "Z", then with AltGr "«".)

All help is greatly appreciated.

[edit]

After many hours of google I found a neat programme called xmodmap which solved the problem.

---

### Post by Guntotingbastard on 2011-05-30
What's the general opinion on bumping?

---

### Post by Guntotingbastard on 2011-05-30
bump

---

### Post by AlphaLexman on 2011-05-30
> **Guntotingbastard said:**
> What's the general opinion on bumping?
Once every 24 hours is enough.

---

### Post by katykat on 2011-05-30
I am not in Ubuntu right now, but under SYSTEM in Preferences or Administation there should be a method for remapping the keys.

I always kill off the CAPS LOCK key, for example.

---

### Post by Guntotingbastard on 2011-05-30
> **AlphaLexman said:**
> Once every 24 hours is enough.
I will remember that.

> **katykat said:**
> I am not in Ubuntu right now, but under SYSTEM in Preferences or Administation there should be a method for remapping the keys.

I always kill off the CAPS LOCK key, for example.

I know under preferences>keyboard>options there are some options to change Caps Lock, and much more. Sadly, it isn't really what I am looking for. I was unable to find any other tool, but I will make sure to extra check.

Thank you both for taking the time to respond.:p

---

