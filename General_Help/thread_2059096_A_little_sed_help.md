---
title: "A little sed help"
date: 2012-09-17
forum: General Help
---

### Post by Drenriza on 2012-09-17
Hey guys and gails.

I have some code as follows
```

for line in `cat downloaded.txt`
do
        sed -i '/$line/d' new.txt
done

```

But for some reason sed cannot delete the line using $line, in it's current state. Simple nothing happens.

How can i edit what i have now so sed can delete the line, or use some other command to accomplish the same goal.

Thanks on advance.
Kind regards.

---

### Post by Lars Noodén on 2012-09-17
You need double quotes so that the shell can interpret $line

```

for line in `cat downloaded.txt`
do
        sed -i "/$line/d" new.txt
done

```

---

### Post by SeijiSensei on 2012-09-17
Another option is to apply "grep -v string" repeatedly to the file.  The "-v" option to grep returns all the lines that do not contain "string".

---

### Post by Drenriza on 2012-09-17
> **Lars Noodén said:**
> You need double quotes so that the shell can interpret $line

```

for line in `cat downloaded.txt`
do
        sed -i "/$line/d" new.txt
done

```

Thanks. I knew the answer was probably right in front of me but i had no idea :p

---

### Post by Vaphell on 2012-09-17
why *cat* with *for* loop?
files should go with *while read*

```
while read -r line; do ...; done < downloaded.txt
```

single sed use
```
sed -i "$( while read l; do printf "/$l/d;"; done < downloaded.txt )" new.txt
```

---

