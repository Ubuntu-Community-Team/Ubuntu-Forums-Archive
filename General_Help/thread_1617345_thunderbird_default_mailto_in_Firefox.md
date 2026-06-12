---
title: "thunderbird default mailto in Firefox"
date: 2010-11-09
forum: General Help
---

### Post by zarathustra@ on 2010-11-09
i have recently came across a problem with the mailto config in firefox.
although in my pc firefox and thunderbird worked out of the box, when i tried to send links from FF in a different pc, thunderbird didn't pop up.
checking Edit > Preferences > Applications, i saw Thunderbird was the selected application in the mailto option. nevertheless, it did not work.
i then tried adding manually through > location bar > about:config. i added a new string just as i found in some internet tutorials, and added /usr/bin/thunderbird. that did not work as well. 

finally, i went back to Edit > Preferences > Applications, and then selected manually  /usr/bin/thunderbird. by the next try, it worked!
i can only guess, that the default choice of thunderbird in that browser was not up to date.
i have noticed, that previous Thunderbird bins were named "mozilla-thunderbird". the current is simply named "thunderbird". maybe that was the reason for this problem??

hope this can help those of you who are having the same problem.

---

