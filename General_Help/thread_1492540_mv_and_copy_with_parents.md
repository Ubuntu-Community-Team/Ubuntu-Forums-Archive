---
title: "mv and copy with parents"
date: 2010-05-24
forum: General Help
---

### Post by morrty11 on 2010-05-24
I always find myself using

```

mkdir -p /parent1/parent2/child

```

to create the parent directories automatically.

What I am wondering is if there is a way to create parent directories with either cp or mv.

It's getting a little repetitive to keep doing

```

mkdir -p /parent1/parent2/child
mv file /parent1/parent2/child

```

---

### Post by Ozymandias_117 on 2010-05-24
The only way I know of to do this is to make a text document with this in it:
```
#!/bin/bash

mkdir -p $2
mv $1 $2
```

then name the file what you want the command to be (I would suggest mvv or mvd as there are no programs you can download from repositories with that name)

After that, type ```
chmod +x *your_text_file* && sudo mv *your_text_file* /bin
``` close and reopen your terminal, and walla, you now have a command!

It will work just like mv does now: (for example) mvv file place

---

### Post by llamabr on 2010-05-25
> **Ozymandias_117 said:**
> close and reopen your terminal, and walla, you now have a command!


[http://en.wiktionary.org/wiki/voil%C3%A0](http://en.wiktionary.org/wiki/voil%C3%A0)

---

### Post by Ozymandias_117 on 2010-05-25
> **llamabr said:**
> [http://en.wiktionary.org/wiki/voil%C3%A0](http://en.wiktionary.org/wiki/voil%C3%A0)

Phonetic spelling ftw. :)

---

