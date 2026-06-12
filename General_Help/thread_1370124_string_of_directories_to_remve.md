---
title: "string of directories to remve"
date: 2010-01-01
forum: General Help
---

### Post by th1bill on 2010-01-01
I have a string of files named recup_dir.1 thru .66. I have the command sudo rm -r /home/"name"/Pictures/recup_dir.1 to remove them one at a time, how do I remove 20 or thirty at one command?

I hope you have mercy on a former Windoze mechanic.

---

### Post by MelDJ on 2010-01-01
a pretty dumb way but...
why not do a search for the files and delete it

---

### Post by garyed on 2010-01-01
What about:

```
sudo rm -r /home/"name"/Pictures/recup_dir.*
```

---

### Post by th1bill on 2010-01-01
> **MelDJ said:**
> a pretty dumb way but...
why not do a search for the files and delete it

Because each f the recup directories have fivee hundred files in each one.

---

### Post by th1bill on 2010-01-01
> **garyed said:**
> What about:

```
sudo rm -r /home/"name"/Pictures/recup_dir.*
```

Thank you sir and I'm writing that down in my personal hand book.

---

### Post by falconindy on 2010-01-01
You could also do:

rm -r /home/"name"/Pictures/recup_dir.{1..66}

And alter to your liking if you only wanted to delete a range, but not all of them.

---

