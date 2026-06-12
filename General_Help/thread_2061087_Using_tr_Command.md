---
title: "Using tr Command"
date: 2012-09-21
forum: General Help
---

### Post by spiritech on 2012-09-21
is there a way to have tr output to the same input file.

so far i have this, and it does work. just figure there may be a easier way.

spiritech@spiritech:~$ ```
cp options options1; tr '\n' ' ' < options1 > options; rm options1
```

this next code works and does not require the creation and deletion of another file.

spiritech@spiritech:~$ ```
echo `cat options` > options
```

if i try to use a similar option as above with tr command it ends up with a blank file

spiritech@spiritech:~$ ```
tr '\n' ' ' < options > options
```

i know the second command solves my problem over all. i am just interested in learning a little more about the tr command.

the reason for the code is to remove newlines and replace with spaces.

so

word 1
word 2
word 3
word 4

into

word 1 word 2 word 3 word 4

spiritech

---

### Post by diesch on 2012-09-21
With *sponge* (package *moreutils*) you can use

```
tr '\n' ' ' < options | sponge options
```

---

### Post by Vaphell on 2012-09-21
tr itself is not that important - you simply can't read and write to the same file simultaneously (what would that be supposed to do anyway?) and this affects most tools.
you have 3 options
- use 2nd file and rename it afterwards
- use some tool that can edit in-place (but in reality uses tmp file either way)
- store everything in memory and then replace the contents in file (which is what echo $(cat file) does)

---

### Post by spiritech on 2012-09-21
> **diesch said:**
> With *sponge* (package *moreutils*) you can use

```
tr '\n' ' ' < options | sponge options
```

I will give this option a go.

---

