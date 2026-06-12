---
title: "deactivate send mail shortcut ctrl-return in evolution 2.28"
date: 2010-09-23
forum: General Help
---

### Post by Carambakaracho on 2010-09-23
Hi Folks,

I'd like to deactivate the shorcut ctrl-return for sending mails in the evolution message composer. I'm frequently using Lyx/Sweave where ctrl/return is used for newlines keeping the previous line's format.

In evolution 2.22 (Ubuntu 8.04) this was done by a simple hack removing the line ```
accel="*Ctrl*Return"
``` from the file /usr/share/evolution/2.22/ui/evolution-message-composer.xml

With 10.04 and evolution 2.28, there is no evolution-message-composer.xml anymore. grep get's no result for .*ctrl.*return.* and return alone does not get any result near a send function.

Any ideas?
Thank you
Carambakaracho

---

### Post by Carambakaracho on 2010-10-12
The solution is actually almost too simple -.- One needs to mouse over the send mail field and hit delete (in Ubuntu 10.04). Simple as that, no hack needed anymore. I got it from the evoution mailing list, but don't remember the precise link anymore.

---

### Post by mjones41 on 2011-06-28
Any updates for this for Evolution 2.30?  I really hate the Crtl return, I accidentally hit it several times a week, I think when I am trying to do a copy paste real fast.  Then I have to apologise for half composed emails at work.

---

