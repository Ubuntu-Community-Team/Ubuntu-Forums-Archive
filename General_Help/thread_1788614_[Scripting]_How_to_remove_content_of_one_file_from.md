---
title: "[Scripting] How to remove content of one file from another"
date: 2011-06-22
forum: General Help
---

### Post by SuaSwe on 2011-06-22
Morning everyone!

I've been puzzling over this for a while and have not been able to reach a solution, so turning to your good selves for advice! I currently have two files, let's say they look like this:

*File A*
```

item1
item3
item5
```

*File B*
```

item1
item2
item3
item4
item5
```

Is there a clever way to "subtract" the content of file A from file B, so that I would be left with everything in file B that is not contained in A (in this case item2 and item4)?

Any help/suggestions much appreciated!

---

### Post by sisco311 on 2011-06-22
Try something like:
```

awk -F'\n' 'NR==FNR{_[$1];next}!($1 in _)' "File A" "File B"

```

---

### Post by SuaSwe on 2011-06-22
Hi sisco311,

Could you explain a bit what that line does? I don't know if it makes a difference but to clarify, the files I'm working with are not as simple as above: they are each several words long and the ones to be removed from file B will not end up being every second one. :)

Also, unfortunately I'm getting syntax error ("near line 1", helpfully enough!) - could it be that it doesn't work with Solaris, which is what I'm working with currently?

---

### Post by erind on 2011-06-22
> **SuaSwe said:**
> ...
Also, unfortunately I'm getting syntax error ("near line 1", helpfully enough!) - could it be that it doesn't work with Solaris, which is what I'm working with currently?

In Solaris use **nawk **or **/usr/xpg4/bin/awk**, not the old awk.
Also *sisco311*'s code will work regardless of the lines' order in File_B (or File_A as well). In case you need the whole line to be removed you might need to replace every** $1 **with **$0**.

---

### Post by sisco311 on 2011-06-22
EDIT: erind beat me to it. :)

I've found the solution here: [http://unstableme.blogspot.com/2008/09/delete-lines-based-on-another-file-awk.html](http://unstableme.blogspot.com/2008/09/delete-lines-based-on-another-file-awk.html)

I'm not very good with awk, but as far as I can tell, it saves the lines from "File A" in an array (the name of the array is _):
```
NR==FNR{_[$1];next}
```
then prints only those lines from "File B" which aren't in the array:
```
!($1 in _)
```

The filed separator is a newline, so $1 is the whole line, but on a second thought, one could use $0, without reseting the FS:
```
mawk 'NR==FNR{_[$0];next}!($0 in _)' filter file
```

Ubuntu uses mawk, but it works in nawk and gawk too.

---

### Post by erind on 2011-06-22
> **sisco311 said:**
> EDIT: erind beat me to it. :)
...

Hey sisco311, I thought you went to sleep ... :)
Your explanation is right on point, also your last code should be fine for the OP, probably he/she needs the whole line, so no need to change the FS.

---

### Post by SuaSwe on 2011-06-23
This does look promising - will try out later!

---

