---
title: "using 'mkdir' cmd"
date: 2010-10-09
forum: General Help
---

### Post by kaykav on 2010-10-09
Hi all,
               Im not sure how to enter a mkdir cmd. Under my home directory, I want to create Dir1 with it having two Directories under it: Dir3 and Dir5. Also under my home directory I want to create Dir2 with it having Dir4 and Dir6.
      So I entered
    $ mkdir -p Dir1/{Dir3,Dir5}; mkdir -p Dir2/{Dir4,Dir6}                

           Is that the shortest cmd I could make?
                            Thanks

---

### Post by nothingspecial on 2010-10-09
```
mkdir -p Dir1/{Dir3,Dir5} Dir2/{Dir4,Dir6}
```

You don`t need the mkdir twice

---

### Post by Vaphell on 2010-10-09
well, you can use single mkdir (space delimits paths to be created)
mkdir -p Dir1/{Dir3,Dir5} Dir2/{Dir4,Dir6}
you can even embed {} parts though no real gain here
mkdir -p ./{Dir1/{Dir3,Dir5},Dir2/{Dir4,Dir6}}

---

### Post by kaykav on 2010-10-09
Thank you ....thats great.........Rich

---

