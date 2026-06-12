---
title: "Could not initialize the package information."
date: 2011-03-01
forum: General Help
---

### Post by Noodle_Boy on 2011-03-01
Hi I'm a first time user of ubuntu and I was trying to install cairo dock and I'm not sure what happened but when I attempted to open the update manager I got this message,

"An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'wget' is not known on line 63 in source list /etc/apt/sources.list'" :(

---

### Post by Verbeck on 2011-03-01
open a terminal (application>accessories) and post the output of the following
```

 cat -n /etc/apt/sources.list

```

---

### Post by Smart Viking on 2011-03-01
What is the output of this, post it here in a code tag or something:
```
cat /etc/apt/sources.list
```You can try to comment out line 63 in that file and see if it helps. To do that launch this:
```
gksudo gedit /etc/apt/sources.list
```but be a little careful with that file.

---

### Post by Noodle_Boy on 2011-03-01
> **Smart Viking said:**
> What is the output of this, post it here in a code tag or something:
```
cat /etc/apt/sources.list
```

You can try to uncomment line 63 in that file and see if it helps. To do that launch this:
```
gksudo gedit /etc/apt/sources.list
```
but be a little careful with that file.

Thank you so much the second worked. I remember typing something in that file by accident.:popcorn:

---

### Post by Smart Viking on 2011-03-01
> **Noodle_Boy said:**
> I remember typing something in that file by accident.
Then why on earth didn't you include that in the first post(no pun intended)? 8-[

---

