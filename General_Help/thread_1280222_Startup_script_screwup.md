---
title: "Startup script screwup"
date: 2009-10-01
forum: General Help
---

### Post by endtime on 2009-10-01
Hi, so I did something foolish...I created a startup script that doesn't return and probably should have been run with &.  Now my boot hangs at "kinit: No resume image, doing normal boot...".  How can I fix this?

Thanks.

---

### Post by j7%&lt;RmUg on 2009-10-01
Boot using your liveCD(if you have one) and try deleting the file that way.

---

### Post by endtime on 2009-10-02
Thanks, I actually managed to boot into a recovery console and throw an ampersand after that line in the script, so the issue's resolved.

---

