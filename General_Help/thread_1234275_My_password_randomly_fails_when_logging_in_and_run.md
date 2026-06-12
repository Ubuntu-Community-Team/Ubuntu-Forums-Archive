---
title: "My password randomly fails when logging in and running the Update Manager"
date: 2009-08-07
forum: General Help
---

### Post by Mr. Cthulhu on 2009-08-07
Recently, Update Manager has been telling me that my password is incorrect when I am prompted to enter it.  It's always worked in the past (I've been running Jaunty about a month now).  This occurs when I log in, too.  Today, my password was rejected 3 times while logging in, but the fourth time it worked just fine.  One time I simply restarted my computer after the password was rejected by Update Manager, and it worked fine when I tried again after that.  So the issue seems to be strangely erratic.

I know for sure that I'm not typing it incorrectly.  It's not an issue with Caps Lock, nor with my keyboard.  My password has never changed.

I hope this question hasn't been asked before, but I had no luck in my searches.  Any help would be hugely appreciated.

---

### Post by yeeeev on 2009-08-07
No straight answer regarding cause, but you could try to change your password to something simpler, as an experiment.
type in
<code>
sudo passwd <username>
</code>
and try to change it to something very simple. Sudo will enable you to override the password strength test.

Obviously, you should change it back to something secure after you'd see that it works fine.

---

