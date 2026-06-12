---
title: "how can regexps be used to exclude a set of strings?"
date: 2010-07-23
forum: General Help
---

### Post by b_k_chu on 2010-07-23
i've been on-and-off familiar with regexps and grep for a few years now, but one thing i've yet to figure out is how to write a regexp so that it will match my pattern *unless* it encounters a specific set of strings within that pattern.

for instance, if i issue:

grep -E "2010-07-23.*TESTUSR.*>(101|100)<" *

then i get every line with that date, TESTUSR, and 101 or 100 between brackets.

but what i want to get is the inverse of that.  sort of.  i want to get every line with that date, TESTUSR, and any 3-digit number between the brackets *except* for 101 or 100.

and i couldn't simply use grep -v since the log files i'm grepping from contain many other usernames and dates, and i don't want to get all those.

i get the feeling that there's probably a simple solution to this that i've either overlooked or just haven't figured out.....but in the past when i've run up against this same type of problem, i've ended up banging my head against it for a few hours, getting a headache, and then giving up. :P

any help or pointers would be appreciated....thanks much.

---

### Post by lloyd_b on 2010-07-24
> **b_k_chu said:**
> i've been on-and-off familiar with regexps and grep for a few years now, but one thing i've yet to figure out is how to write a regexp so that it will match my pattern *unless* it encounters a specific set of strings within that pattern.

for instance, if i issue:

grep -E "2010-07-23.*TESTUSR.*>(101|100)<" *

then i get every line with that date, TESTUSR, and 101 or 100 between brackets.

but what i want to get is the inverse of that.  sort of.  i want to get every line with that date, TESTUSR, and any 3-digit number between the brackets *except* for 101 or 100.

and i couldn't simply use grep -v since the log files i'm grepping from contain many other usernames and dates, and i don't want to get all those.

i get the feeling that there's probably a simple solution to this that i've either overlooked or just haven't figured out.....but in the past when i've run up against this same type of problem, i've ended up banging my head against it for a few hours, getting a headache, and then giving up. :P

any help or pointers would be appreciated....thanks much.

Your problem is conceptual - you're trying to do in one command something that's logically two different things.  The solution is to do one "grep" command to get all the "TESTUSR" lines for that date, and then pipe that to a second "grep", using the "-v" option this time to exclude the 100 and 101 lines.

I *think* this will do what you want:```
grep -E "2010-07-23.*TESTUSR.*>[0-9][0-9][0-9]<" * | grep -Ev ">(100|101)<"
```where the first "grep" gets any line for that date with TESTUSR and a 3 digit number between the angle brackets, and the second grep then filters out the lines with 100 and 101 between the brackets.

Lloyd B.

---

### Post by b_k_chu on 2010-07-28
and there it is...the simple solution that just hadn't occurred to me.  i haven't had a chance to try it out yet, but i'm certain that it's just what i need.

thanks much, Lloyd. :3

---

