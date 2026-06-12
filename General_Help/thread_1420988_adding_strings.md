---
title: "adding strings"
date: 2010-03-03
forum: General Help
---

### Post by sandyd on 2010-03-03
How do you add strings to the front and end of variables in bash scripting?

for example, if I have ```
in
``` as the contents of my variable, I want to add "l" to the front and "k" to the back of the contents.

---

### Post by kaibob on 2010-03-03
Probably an easier way to do this, but you can use parameter expansion:

> $ var=in ; var=${var/#/l} ; var=${var/%/k} ; echo $var
link

---

