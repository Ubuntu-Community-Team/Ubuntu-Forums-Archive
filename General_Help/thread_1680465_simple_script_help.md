---
title: "simple script help"
date: 2011-02-02
forum: General Help
---

### Post by jlparsons on 2011-02-02
Hi folks, here's what I want to do but cannot...

Shell reads a variable which contains several words separated by spaces.  Shell makes a copy of a file named after the variable, all words including spaces.  Here's what I've got so far:

echo "Enter Client Surname"
read sirname
echo "Enter Client Forenames"
read forename
cp -n /home/blah/.NewClient.ods /home/blah/$sirname\ $forename.ods

This works a treat as long as each variable is one word only.  In the case of multiple words it doesn't do anything.  Any ideas?  You may have guessed I'm totally new to this...

Cheers,

James

---

### Post by gmargo on 2011-02-03
Try using some quotes:
```

cp -n /home/blah/.NewClient.ods "/home/blah/$sirname $forename.ods"

```

---

### Post by jlparsons on 2011-02-03
> **gmargo said:**
> Try using some quotes:
```

cp -n /home/blah/.NewClient.ods "/home/blah/$sirname $forename.ods"

```

Worked a treat.  Quotes around each variable.  Many thanks!

---

