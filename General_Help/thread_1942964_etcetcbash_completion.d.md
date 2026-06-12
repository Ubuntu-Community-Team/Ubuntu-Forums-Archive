---
title: "/etc/etc/bash_completion.d ???"
date: 2012-03-18
forum: General Help
---

### Post by kosajaffe on 2012-03-18
Hi there,

today I stumbled upon a /etc/etc/bash_completion.d folder with two files in it:

gdbus-bash-completion.sh
gsettings-bash-completion.sh

Two questions:
1. Why I have /etc/etc at all?
2. What are these two files good for?

To me it looks like an update or installation failed.
There should be no such folder as /etc/etc, right?

Cheers and thanks in advance.

---

### Post by kosajaffe on 2012-03-19
Seems like there is already a bug report for this issue. See: [https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/819171](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/819171)

Solution: just move the two files into /etc/bash_completion.d where they belong and delete the wrongly created folders.

---

