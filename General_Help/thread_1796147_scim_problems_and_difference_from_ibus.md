---
title: "scim problems and difference from ibus"
date: 2011-07-03
forum: General Help
---

### Post by mobius129a on 2011-07-03
Basically, I want to know the difference in function between scim and ibus.

In order to be able to input Chinese characters, I have done the following:
1. installed scim and scim-pinyin packages.
2. installed language packs 
3. locale configuration ```
im-switch -z en_US -s scim
```.However, I was unable to input Chinese characters until I activated the ibus daemon. Subsequently, in order to input Chinese characters I do it via the IBus icon in the system tray. Since IBus seems to be doing the job just fine, I haven't tried to get scim working. 

Any idea why scim isn't working? 
What's the difference between scim and ibus; is one recommended over the other?

---

### Post by mobius129a on 2011-07-04
bump.

---

### Post by wenfuli on 2011-07-08
I can't tell you the difference between scim and ibus, but I do know that to input Chinese, using ibus is better. That's what I used before; it was the only way I could get Chinese to work properly. Right now I'm searching how to start the ibus daemon, as I just did a complete re-install of Ubuntu and ibus has not started by itself.

---

### Post by mobius129a on 2011-07-09
I managed to activate the ibus-daemon in a way that's similar to what's outlined [here]("http://ubuntuforums.org/showthread.php?t=1310674#14") . Hope that helps.

---

