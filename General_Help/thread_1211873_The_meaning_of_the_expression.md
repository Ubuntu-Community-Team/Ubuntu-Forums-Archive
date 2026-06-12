---
title: "The meaning of the expression"
date: 2009-07-13
forum: General Help
---

### Post by jiraaya on 2009-07-13
What is the meaning of the following expression?
**$ECLIPSE_HOME/eclipse $* **

---

### Post by ibutho on 2009-07-13
$ECLIPSE_HOME would be where the eclipse installation directory is located e.g. /opt/eclipse. $ECLIPSE_HOME/eclipse would be the eclipse program located in $ECLIPSE_HOME e.g. /opt/eclipse/eclipse.

---

### Post by geirha on 2009-07-13
And $* will expand to all arguments provided to the script. It's more common to use "$@" instead of $* though, as "$@" will properly handle spaces in arguments.

---

