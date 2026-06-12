---
title: "alias - scp"
date: 2010-03-11
forum: General Help
---

### Post by CptBlack91 on 2010-03-11
Hi,
I regularly need to copy files from a remote computer to wherever I am working. I've ben looking into alias and the .bashrc (or .profile in the remote computer - mac)
Can I use scp in these files?
I've tried:
```
alias='sch usr@location:'
```then when in the local terminal:
```
sch path/file .
```But this doesn't work.

Better would be copying when logged into the remote location, but I haven't figured that out in terminal yet, let alone an alias for it.

Hopefully it'll be a quick solution!

Cheers,
C

---

### Post by gmargo on 2010-03-11
Syntax of alias:
```

alias sch='scp user@location'

```Oops, sorry that won't work.  It's more difficult if there can't be a space.  Try a shell function, something like
```

sch()
{
    scp usr@location:"$1" "$2"
}

```

---

### Post by CptBlack91 on 2010-03-11
Brilliant, cheers!
Works perfectly, and is going to save so much time!

C

---

### Post by CptBlack91 on 2010-03-12
A couple more questions along the same lines:
When I change to a new directory, I often want to see whats in there, so I cam up with the following which works on macs, but not on linux it seems (it lists the files in the desired directory but then I'm no in that directory)
```
alias cdl='cd ; ls -a'
```

Secondly, I want to regularly save my command history based on the date, I've tried several things to get this to work, but can't yet. Any help?
```
hist()
    {
        history    > "history/history_" date +%y "_" date +%m "_" date +%d ".txt"
    }
```

---

### Post by cjhabs on 2010-03-12
For the cdl biy, use a bash function in .bashrc:
cdl() {
	cd $1
	ls -a
}

---

### Post by cjhabs on 2010-03-12
> **CptBlack91 said:**
> A couple more questions along the same lines:
When I change to a new directory, I often want to see whats in there, so I cam up with the following which works on macs, but not on linux it seems (it lists the files in the desired directory but then I'm no in that directory)
```
alias cdl='cd ; ls -a'
```

Secondly, I want to regularly save my command history based on the date, I've tried several things to get this to work, but can't yet. Any help?
```
hist()
    {
        history    > "history/history_" date +%y "_" date +%m "_" date +%d ".txt"
    }
```

Make sure that ~/history folder already exists

For hist, try this:
```

history > ~/history/history_$(date +%y)_$(date +%m)_$(date +%d).txt
```

---

### Post by gmargo on 2010-03-12
```
hist()
{
    local file="$HOME/history/history_"$(date +%y)"_"$(date +%m)"_"$(date +%d)".txt"
    history > "$file"
}
```

---

