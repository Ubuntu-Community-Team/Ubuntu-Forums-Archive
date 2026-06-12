---
title: "Script Required for Manipulating Directory Names"
date: 2012-09-05
forum: General Help
---

### Post by buster2209 on 2012-09-05
I'm looking for a simple bash script that I can execute that will strip the first 5 chars of *each* folder name in a given folder.

Any ideas?

---

### Post by steeldriver on 2012-09-05
something like 

```
find . -type d -exec rename -nv 's/.{5}//' {} \;
```maybe? remove the -n option when you've got the match working right

You can add a -maxdepth to the find if you don't want it to descend recursively, or just

```
rename -nv 's/.{5}//' */ 
```

to just rename directories directly below the current dir

---

### Post by Lars Noodén on 2012-09-05
That munges the beginning of the paths!

Here's a variant:

```

find /some/path/ -type d -exec rename -nv 's/\/[^\/]{5}([^\/]*)$/\/$1/' {} \;

```

Edit: thanks steeldriver, it's now corrected.

---

### Post by steeldriver on 2012-09-05
oops you're right - thanks for the correction Lars!

EDIT: I think the regex might need something to explicitly catch the trailing part though?

```
's/\/[^\/]{5}([^\/]*)$/\/$1/'
```

---

### Post by buster2209 on 2012-09-05
Thanks, I will try this later

---

