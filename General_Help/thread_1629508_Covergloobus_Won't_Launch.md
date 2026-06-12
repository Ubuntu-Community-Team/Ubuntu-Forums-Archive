---
title: "Covergloobus Won't Launch"
date: 2010-11-23
forum: General Help
---

### Post by zacharyh on 2010-11-23
I installed covergloobus and it was working for a bit, but now it won't launch. I select it from the menu, no response. I run it from ALT+F2, no response. 

When I type covergloobus in the terminal, it responds that it is already running - but I can't see it.

When I type killall covergloobus, it tells me that no process was found.

Can anyone help? I'm running 10.10 and downloaded the 1.7 deb, which I have reinstalled multiple times to no avail.

Thanks!

---

### Post by zacharyh on 2010-12-05
Bump

---

### Post by HelloIndustries on 2011-02-03
Came here looking / hoping for a solution, but no one has replied.

Anyway, i did a little googling, and [found the bug report here]("https://bugs.launchpad.net/covergloobus/+bug/583137").
That solution didn't work for me as i had no covergloobus folder or config file in ~/.config/CoverGloobus/CoverGloobus.cfg

**What DID work for me** -and hopefully for you, too- is: 
Go to <username>/.covergloobus and make sure you own, and have full access to [I]CoverGloobus.lock

[/I]I hope this helps if you've haven't already solved it / worked around / given up
:)

---

