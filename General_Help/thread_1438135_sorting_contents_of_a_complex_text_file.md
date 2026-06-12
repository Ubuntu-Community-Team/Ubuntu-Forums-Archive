---
title: "sorting contents of a complex text file"
date: 2010-03-24
forum: General Help
---

### Post by pokeyThePenguin on 2010-03-24
I have a text file that's 3688 lines long, so I don't want to sort it by hand. The file has 2 formats:

foo space/tab bar space/tab blah

and

blah

I have these lines split into categories, so I can't sort the entire file in one go, I need to sort from line N to line M, and just keep doing that until everything is sorted.

Is there a way to say: sort all lines from line N to line M. If line has 3 or more columns, use 3rd column for sorting. If line has 1 column, use that.


Let's say we have an unsorted file:
```

--------------
first category
--------------

carrot = vegetable
apple = fruit
chicken = meat
dairy

---------------
second category
---------------

green
orange
sun = yellow
sky = blue

```

I would want the result to be:

```

--------------
first category
--------------

dairy
apple = fruit
chicken = meat
carrot = vegetable

---------------
second category
---------------

sky = blue
green
orange
sun = yellow

```

---

### Post by jm2 on 2010-03-24
I know part of your answer. To select just a few lines from your file

sed -n '5,8p' <your_file> > <output file>
This selects lines 5, 8 and puts them into output file.

Then you can do a sort.

[http://lowfatlinux.com/linux-sort.html](http://lowfatlinux.com/linux-sort.html) 
is where I figured out you can do

sort +1 -1 <output file> > <sorted-file>

hopefully this will point you in the right direction.

Good luck

---

