---
title: "CUPS and Password"
date: 2012-06-10
forum: General Help
---

### Post by ExSuSEusr on 2012-06-10
Trying to set up network printing.

Going to  [http://localhost:631/admin/](http://localhost:631/admin/)  

It wants a usr and password.  Which ahhhh I never set.  I tried my log / pass - tried root - nothing works.

Is there a default login and password?

NEVER MIND: Figured it out

  lppasswd -g <group> -a <user>
 
  lppasswd -g sys -a root

---

