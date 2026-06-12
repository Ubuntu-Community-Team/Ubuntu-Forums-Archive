---
title: "Disable caps lock?"
date: 2009-07-06
forum: General Help
---

### Post by Cephi on 2009-07-06
My eee pc keyboard got stupid and decided that I'm forever holding down the tab key.  So I used xev to find the key codes for the tab and caps lock keys, and I used xmodmap to (i) disable the tab key and (ii) map the caps lock key to function as the tab key.  It works just fine... almost.  In addition to tabbing, the caps lock key still toggles caps lock.  I want it only to tab, and not to toggle caps.  How can I do that?  Can I use xmodmap for that?  Ideas?

---

### Post by michy99 on 2009-07-06
Maybe you can map some key that you never use as the Caps Lock.

---

### Post by Cephi on 2009-07-06
> **michy99 said:**
> Maybe you can map some key that you never use as the Caps Lock.

Hmm, I tried remapping a couple keys to function as caps lock.  As far as xev is concerned, they are now caps lock.  But they don't function as caps lock.  And of course this did not solve the problem, that my caps lock key still toggles caps lock (even though it is also functioning as tab key).

---

### Post by Cephi on 2009-07-06
Got it!  I first tried to run
> xmodmap -e 'remove Lock = Caps_Lock'
since reading the xmodmap man led me to believe that this would remove caps lock functionality from the caps lock key.  It didn't work.  But then I realized this was because I needed to run
> xmodmap -e 'remove Lock = Tab'
since, as far as xmodmap was concerned, my caps lock key was now my tab key!  the second command got me where I needed to go.

(unfortunately the first time i did it, my caps lock was on, so i wound up with caps lock on and no way to turn it off! i had to sheepishly undo what I'd done, toggle caps lock, and then redo it ^-^)

EDIT: hey, isn't it kind of weird that you don't need sudo to run these xmodmap commands?

---

