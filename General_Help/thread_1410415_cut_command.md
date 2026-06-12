---
title: "cut command"
date: 2010-02-18
forum: General Help
---

### Post by ryanf4321 on 2010-02-18
i'm trying to write a script that takes just once section out of df -lh / (the number of Available disk space) and was wondering how to get just the number, without the Avail part.

right now i have 

        df -lh / | cut -c 34-38 

but that gives avail XXX.

That almost gives me what i want, but i need just the number because i'm going to use the result as a variable for my script.

can anyone tell me how to use cut to do this, or if there's an easier command i should be using.

Thanks in advance.

---

### Post by sisco311 on 2010-02-18
try:
```
df -lh / | awk '$4!="Avail"{print $4}'
```

---

### Post by ryanf4321 on 2010-02-18
Thanks! that seems to work.

---

### Post by dcstar on 2010-02-19
> **ryanf4321 said:**
> i'm trying to write a script that takes just once section out of df -lh / (the number of Available disk space) and was wondering how to get just the number, without the Avail part.

right now i have 

        df -lh / | cut -c 34-38 

but that gives avail XXX.

That almost gives me what i want, but i need just the number because i'm going to use the result as a variable for my script.

can anyone tell me how to use cut to do this, or if there's an easier command i should be using.

Thanks in advance.

```
df -lh / | cut -c 33-37 | tail -1
```

---

### Post by rnerwein on 2010-02-19
> **sisco311 said:**
> try:
```
df -lh / | awk '$4!="Avail"{print $4}'
```

hi
for world wide usage ( language ) try

df -lh | awk 'FNR != 1 {print $4}'

ciao :-)  :_)

---

### Post by cong06 on 2010-02-19
> **ryanf4321 said:**
> i'm trying to write a script that takes just once section out of df -lh / (the number of Available disk space) and was wondering how to get just the number, without the Avail part.

right now i have 

        df -lh / | cut -c 34-38 

but that gives avail XXX.

That almost gives me what i want, but i need just the number because i'm going to use the result as a variable for my script.

can anyone tell me how to use cut to do this, or if there's an easier command i should be using.

Thanks in advance.

well, I'm not very familiar with the '-c' command with cut.
There's always sed:
```

        df -lh / | cut -c 34-38 | sed -e 's/[a-z]//gi'

```
The one drive which is 19 GB though now only shows 19. But I guess you can manage that.

Edit: I think I read something wrong. The awk command is much better anyway.

---

