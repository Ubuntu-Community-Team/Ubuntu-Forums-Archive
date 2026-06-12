---
title: "Find and Delete specific folders?"
date: 2011-09-28
forum: General Help
---

### Post by PDA1 on 2011-09-28
I want to find and then delete specific folders with the name of "tn"

How do I do it....quickly?

Thanks.

---

### Post by geo909 on 2011-09-28
Yup, you could do that quickly from the command line.

You could do something like:

```

find . -name tn -exec rm -rf {} \;

```

From within the folder where your tn files are (recursively).

**I would strongly suggest that you first run a single find 
command to see what you would delete with the code above!!**

```

find . -name tn

```

or even better, if you don't have too many tn files, you could just do

```

find . -name tn -exec rm -rfi {} \;

```

to do it interactively (you'd have to give a "y"
to confirm every deletion).

Check this for instance or google around 
"find command delete files linux" or something
like that.

Hope that helps

---

### Post by OpEn_SoUrCe_RoCkS on 2011-09-28
Theoretically this could be achieved by issuing this command in a shell:

```
find /path/ -type d -name &#8220;tn" -exec rm -r {} \;
```

Where /path/ is the path to the folder containing all the directories you're looking to delete.

As per usual, though, be careful with "rm" :D

EDIT: Damn it, beaten to the punch!! ;)

---

