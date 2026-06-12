---
title: "Firefox does not autocomplete after coming back from sleep"
date: 2010-10-18
forum: General Help
---

### Post by kelper on 2010-10-18
Hello,
My Ubuntu goes to sleep after 5 minutes. When I wake it up, and enter Firefox, and try to type in an address, it does not bring the dropdown menu with the history of the URLs that begin with the string I just typed. Is there anyway to get it to stop forgetting the history after Ubuntu comes back from sleep?

---

### Post by lovinglinux on 2010-10-18
Does it cleanup the History when you simply close Firefox and open it again?

---

### Post by kelper on 2010-10-19
Yes, I have it remember my history for up to three days. And "Clear history when Firefox closes" is unchecked.

---

### Post by mordoc on 2010-10-19
I've been noticing this for back to 10.04. I just assumed that it is a feature of FF with some thread not being able to wake up again after resume. I don't believe there is a "fix" for this...

Here's a thread of an earlier discussion on this:

[http://ubuntuforums.org/archive/index.php/t-1469046.html](http://ubuntuforums.org/archive/index.php/t-1469046.html)

Final edit:

[https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/438868](https://bugs.launchpad.net/ubuntu/+source/indicator-session/+bug/438868)

This bug report indicates that the workaround is to minimize and restore the app...

---

