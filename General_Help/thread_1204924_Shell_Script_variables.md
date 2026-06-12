---
title: "Shell Script variables"
date: 2009-07-05
forum: General Help
---

### Post by contecarli on 2009-07-05
Hi!

I'm trying to set a command including an input redirect as a variable in a shell script.

The normal command would be:
```

#!/bin/sh

otherapp -c /path/to/application < inputfile

```This works fine.

Now I want to set the command parameter as a variable:
```

#!/bin/sh

app="/path/to/secondapp < inputfile"

firstapp -c $app

```If I use it in this way, the firstapp recognises the app variable as three input arguments instead of using it as one command.

How can I solve this?

Thanks in advance,
contecarli

---

### Post by Boondoklife on 2009-07-05
[FONT=monospace]try
```
[/FONT]#!/bin/sh

app="/path/to/secondapp < inputfile"

firstapp -c "$app"
```

---

### Post by Johnny B on 2009-07-05
i dont know what apps you're talking about but i think the value of your variable should be in backquotes:
> j$ DATE="date +%m/%d%Y"
$ echo $DATE
date +%m/%d%Y
$ DATE=`date +%m/%d%Y`
$ echo $DATE
07/052009


---

### Post by t4thfavor on 2009-07-05
No, "back quotes" are for shell commands. in your example the script will run the date command and set the variable to the output of said command.

The first example should work fine though.

---

### Post by geirha on 2009-07-05
I don't think there is any way to do what you want (except with eval). I recommend you use two variables instead.
```

app="/path/to/secondapp"
file="inputfile"

firstapp -c "$app" < "$file"

```

---

### Post by Johnny B on 2009-07-05
what apps are we talking about here?

---

### Post by loomsen on 2009-07-06
```

echo -c $(ls < /opt)

```

otherapp -c $(app < input)

*edit*

don't even need -c

> 
docter[~] echo "/opt" >> tmp 
docter[~] grep op < tmp
/opt
docter[~] cd $(grep op < tmp)
docter[/opt] ls


---

