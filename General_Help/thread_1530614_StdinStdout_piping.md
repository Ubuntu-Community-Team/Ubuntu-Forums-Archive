---
title: "Stdin/Stdout piping"
date: 2010-07-13
forum: General Help
---

### Post by hwong557 on 2010-07-13
Hi,

I'm just starting to pipes in Linux. One thing I would like to do is take the output from a command and send it to another command. For example, I usually run:

```
$which script-name
/some/path/script
$less /some/path/script
*contents of script*

```

How would I use pipes to make this happen? I try ```
less < which script-name
``` but that just gives me "bash: which: No such file or directory". 

```
which script-name | less

``` gives me just the path to the script.

Thanks for your help!

---

### Post by amauk on 2010-07-13
```
less < $(which script-name)
```

---

### Post by gmargo on 2010-07-13
For the traditionalist, this is what backticks are for.
You could use the $() form as well.
```

$ less `which script-name`

$ less $(which script)

```

---

### Post by hwong557 on 2010-07-13
Thanks guys! That was quite helpful. It seems that the $ identifies "which script-name" as a variable and not as something else. Thanks guys!

---

