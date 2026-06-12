---
title: "Firefox Gmail Issues"
date: 2011-09-20
forum: General Help
---

### Post by kerryhall on 2011-09-20
When I try to load Gmail in firefox, I get this:

[http://i.imgur.com/N6cCJ.png](http://i.imgur.com/N6cCJ.png)

Started happening about a week ago. I disabled all addons and extensions, but that didn't help. Version 3.6.22.

---

### Post by MWGod on 2011-09-20
Try clearing your cache and/or flushing your DNS :popcorn:

---

### Post by papibe on 2011-09-20
Running the same version here (with no problems).

Things that I would try:
[LIST]
[*]Clear recent history.
[*]Load Firefox in Safe Mode (firefox -safe-mode).
[*]Creating a new profile to see if the error persists (firefox -ProfileManager, and then firefox -P newprofile)
[/LIST]
Hope it helps,
Regards.

---

### Post by kerryhall on 2011-09-20
Creating a new profile did the trick. So now I need to figure out what it is about my default profile that screws everything up.

Interestingly enough, when I tried clearing the cache, nothing happened. I could click the button and there was no message, nothing to indicate that anything had been done. 

Also, I noticed that in the profile that is messed up, when I try to sell an item on eBay and toggle back and forth between standard view and HTML view in the item description, the changes made in HTML mode are not saved when returning to standard view. Quite infuriating. Perhaps this indicates that there is a problem with cookies, java, javascript, or one of those sorts of things. 

Thanks!

---

### Post by kerryhall on 2011-09-28
Alright, so making a new profile fixes the problem, but now I have to switch back and forth between two profiles, as my original one has all my bookmarks, etc. which is annoying to say the least.

Any idea how to fix the original profile? What could be causing this problem?

Thanks!

---

### Post by papibe on 2011-09-28
Close all firefox windows. Then run:
```
$ firefox -P the_one_needed_fixing  -safe-mode
```
You'll be presented with several options (that I can't remember), but one of them would be something like 'reset profile'.

The only con of this is that you may need to reinstall, or reconfigure, your plugins.

Hope that helps,
Regards.

---

### Post by kerryhall on 2011-10-05
Thank you! I ran it in safe mode, and checked every box except "reset bookmarks" and that fixed it! thanks again!

---

