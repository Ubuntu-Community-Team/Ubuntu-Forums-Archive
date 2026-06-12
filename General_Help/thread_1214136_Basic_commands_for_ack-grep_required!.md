---
title: "Basic commands for ack-grep required!"
date: 2009-07-15
forum: General Help
---

### Post by Rytron on 2009-07-15
Hi.
Can someone put a up a quick tutorial on some basic commands for ack-grep?
Thanks.

---

### Post by Rytron on 2009-09-05
Anyone?

---

### Post by dandnsmith on 2009-09-05
There is a list of flags for the command [here](http://betterthangrep.com/).

HTH

---

### Post by Rytron on 2009-09-05
> **dandnsmith said:**
> There is a list of flags for the command [here](http://betterthangrep.com/).

HTH

Much appreciated dandnsmith.

---

### Post by Rytron on 2009-09-06
Hi.
I want an ack-grep command that will ignore certain directories.

For example I want to ignore the hidden files (.*) in the home directory. I am starting the search from my home directory.

Would I need something like this?
```
ack-grep -ai [COLOR="Sienna"]Tiger[/COLOR] --ignore-dir=/home/rytron/.*
```

Or if I want to ignore searching the Desktop.
Would I require something like this?
```
ack-grep -ai [COLOR="Purple"]Panther[/COLOR] --ignore-dir=/home/rytron/Desktop
```

:confused:

---

### Post by dandnsmith on 2009-09-06
That sounds like the right sort of thing - I'd try it to see if it works.

---

### Post by Rytron on 2009-09-06
It doesn't seem to work. It is not ignoring the directories I want it to ignore. I must have the wrong syntax somewhere.

---

### Post by scragar on 2009-09-06
```
ack -ai Tiger -G '^[^\.]'
```
Might work to ignore files beginning with . but I cannot be sure.

---

### Post by Rytron on 2009-09-06
> **scragar said:**
> ```
ack -ai Tiger -G '^[^\.]'
```
Might work to ignore files beginning with . but I cannot be sure.

Yes, does work. I had to add '-grep' to get it to work.

```
ack-grep -ai Tiger -G '^[^\.]'
```

---

