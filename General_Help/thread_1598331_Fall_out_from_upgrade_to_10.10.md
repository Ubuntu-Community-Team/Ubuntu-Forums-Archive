---
title: "Fall out from upgrade to 10.10"
date: 2010-10-16
forum: General Help
---

### Post by Robbyx on 2010-10-16
What does this mean?

> E: prelude-lml: subprocess installed post-installation script returned error exit status 1


---

### Post by sikander3786 on 2010-10-16
[http://www.google.com.pk/search?q=E%3A+prelude-lml%3A+subprocess+installed+post-installation+script+returned+error+exit+status+1+&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com.pk/search?q=E%3A+prelude-lml%3A+subprocess+installed+post-installation+script+returned+error+exit+status+1+&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

When do you get that error?

---

### Post by Robbyx on 2010-10-16
I get the error message when I run the partial upgrade from the update manager.

---

### Post by Zhukov on 2010-11-10
Sorry for double posting, but...

Guys, here is the fix:

sudo prelude-admin register "prelude-lml" "idmef:w" 127.0.0.1 --uid 0 --gid 0

I used the localhost as the manager address. This should be added to post-install script.

=) Enjoy!

Posted bugfix here as well:
[https://bugs.launchpad.net/ubuntu/+source/prelude-lml/+bug/628692](https://bugs.launchpad.net/ubuntu/+source/prelude-lml/+bug/628692)

---

