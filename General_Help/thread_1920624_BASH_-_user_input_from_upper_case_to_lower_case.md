---
title: "BASH - user input from upper case to lower case"
date: 2012-02-05
forum: General Help
---

### Post by iMetaphysikz on 2012-02-05
```

#!/usr/bin/bash
        echo -n "Please enter yes or no (y/n)?"
        read yesno
        yesno="$yesno | tr '[A-Z]' '[a-z]'"
        echo $yesno

```Please enter yes or no (y/n)?y
Y | tr '[A-Z]' '[a-z]'

As you can see echo is producing the command I want to run, instead of the output of the command I wanted to run.

Any ideas?

---

### Post by Khayyam on 2012-02-05
iMetaphysikz ...

something like ..

```
#!/bin/bash

function ask()
{   
    echo -n "$@" '[y/n] ' ; read ans
    case "$ans" in
        y*|Y*) return 0 ;;
        *) return 1 ;;
    esac
}

ask "Please enter: yes or no?" && echo "You said yes!!!"
```[Y|y]es executes (the 'echo'), [N|n]o does nothing.

HTH ..

---

### Post by mcduck on 2012-02-05
That's because you are setting the variable's value to string, instead of running a command and setting the variable to the command's result.

(also the command you are trying to use is missing a part, you need to echo the $yesno to the pipe, simply having a variable's name there does nothing. And Bash is located in /bin/bash... ;))
```

#!/bin/bash

echo -n " Please enter yes or no (y/n)?"
read yesno
yesno=$(echo $yesno | tr '[A-Z]' '[a-z]')
echo $yesno
```

---

### Post by iMetaphysikz on 2012-02-05
Thanks Khayyam and mcduck.

Mcduck, thanks for showing me what I was doing wrong and pointing me in the right direction.
Khayyam, Thanks for showing me an alternative way, with functions that I may adjust and implement later.

---

### Post by Khayyam on 2012-02-06
iMetaphisikz ... your very welcome

I confess I didn't read your code, but saw what you were try to do and answered with a function I use for this kind of thing. Not exactly the best response as it side steps the actual problem and doesn't allow you to learn .. mia culpa.

Anyhow, what mcduck means by "setting the variable to the command's result" is what is commonly called "command substitution", the output of the command is "substituted" in place of the command .. for this we place the command within "$( )" eg:

```
% echo $(date +%F)
2012-02-06
% TODATE=$(date +%F)
% echo ${TODATE}
2012-02-06
```

Note that I place the variable within currly braces, this is not necessary but means we can do something like the following ..

```
#!/bin/bash

YEAR=$(date +%Y)
MONTH=$(date +%m)
DAY=$(date +%d)

echo ${YEAR}-${MONTH}-${DAY}
```

HTH ..

---

