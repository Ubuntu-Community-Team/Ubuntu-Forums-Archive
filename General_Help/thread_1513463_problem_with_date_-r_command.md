---
title: "problem with date -r command"
date: 2010-06-19
forum: General Help
---

### Post by Sylos on 2010-06-19
Hello there.
Im trying to get into bash scripting and as part of my practice Im trying to get a variable in my script to be determined by the date a file was last modified. This variable should then be echoed. Here is the lines I am using:

```
#!/bin/bash

#backup only if existig backup up more than 1 hour old

a=date -r /home/saric/backup

echo $a
```

unfortunately when I run it I am getting the following output:

```
......line 5: -r: command not found

```

Having looked at the arguments list for the date command i cant understand it. It should be a valid command like that.

I tried enclosing the date -r /home/saric/backup in brackets but it just seemed to escape the special meaning of the date command and printed "date" to me as the echo part.

Any insight gratefully received.

---

### Post by Zip247 on 2010-06-19
I read the man page wrong, disregard this post as i can not figure out how to delete it.

---

### Post by ciscosurfer on 2010-06-19
> **Sylos said:**
> [*snip*]```
#!/bin/bash

#backup only if existig backup up more than 1 hour old

a=[COLOR="Red"]**$(**[/COLOR]date -r /home/saric/backup[COLOR="red"]**)**[/COLOR]

echo $a
```[*snip*]Sylos, you'll want to look up command substitution. Here's a quick guide: [http://www.gnu.org/software/bash/manual/bashref.html#Command-Substitution](http://www.gnu.org/software/bash/manual/bashref.html#Command-Substitution)

You need to use $(*command*) or `*command*` -- backticks are deprecated in Bash 4.0 I believe, but can still be used. The newer convention is $(*command*).

---

### Post by Sylos on 2010-06-21
Thanks for the post. That now works.

Easy and obvious when someone points it out.

Many Thanks

---

