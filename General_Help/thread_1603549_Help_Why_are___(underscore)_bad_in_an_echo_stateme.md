---
title: "Help: Why are _ (underscore) bad in an echo statement?"
date: 2010-10-22
forum: General Help
---

### Post by leesiulung on 2010-10-22
Why are underscores bad in a script?

The below script only prints out part2...?

```

#!/bin/sh
read part1
read part2

echo "$part1_$part2"

```

Since I can't use - (dashes) in MySQL database names, I'm limited to using _ (underscores). However, my dash script refuses to work with underscores.

Any suggestions?

---

### Post by sgosnell on 2010-10-22
What are you expecting the underscore to do?  It looks as if you want to concatenate part1 & part2, and I don't think an underscore is going to give that result.

[This page](http://desk.stinkpot.org:8080/tricks/index.php/2007/02/concatenate-strings-in-bash/) gives some good information on concatenating strings.

---

### Post by efflandt on 2010-10-22
Either of these work depending whether you want the combined string to be a variable.

```
#!/bin/sh
read part1
read part2

echo "$part1"_"$part2"
``````
#!/bin/sh
read part1
read part2
parts=$part1"_"$part2
echo "$parts"
```

---

### Post by leesiulung on 2010-10-23
The underscore is a separator instead of a space between the contents of part1 and part2. That is what I was trying to do, instead I only got part of the string.

I will give the other suggestions a try.

edit: It looks like "$part1"_"$part2" works, but what gives? Is underscore special?

---

### Post by kalos on 2010-10-23
The underscore is interpreted as part of the variable name (so you can have names like $underwater_camera. So bash thinks you're using a variable named $part1_ 

Try this:
```
#!/bin/sh
read part1
read part2

echo "${part1}_${part2}"
```

---

### Post by kalos on 2010-10-23
> **leesiulung said:**
> It looks like "$part1"_"$part2" works, but what gives? Is underscore special?

The underscore isn't special (you'd get the same result if you used a letter instead of the underscore), it's the quotes that are special. However, when interpolating variables into a string, it's more common to use {squiggly brackets} to separate the variables from the text.

---

