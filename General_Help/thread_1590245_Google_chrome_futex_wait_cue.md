---
title: "Google chrome futex wait cue"
date: 2010-10-07
forum: General Help
---

### Post by mik9dt on 2010-10-07
I have struggled to get google chrome browser running for the last few months. I had been using it for months with no problem, and then, one particular upgrade and it kept eating 100% cpu and being totally unresponsive. I have tried many things, none of them worked.
Then I noticed that on a test profile in ubuntu chrome behaved itself. But not on my main profile.... Hmmmm?

Eventually I have done what I should have done in the first place.

try deleting

 ~/.config/google-chrome

 ~/.cache/google-chrome

Hooray, success, it works!

If you sync your gmail account via google, then all your bookmarks, etc. will be restored on a first run of chrome on your now clean system. Easy when you know how. Something in the inherited google settings was throwing chrome into a loop.

I wish I had known this months ago.

---

