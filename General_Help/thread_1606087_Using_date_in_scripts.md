---
title: "Using date in scripts"
date: 2010-10-26
forum: General Help
---

### Post by wurlyfan on 2010-10-26
I am trying to use the date command in a simple bash script as below:

#!/bin/sh

this_date=`date`

echo "The date is $this_date"

This script seems to work only if a surround the command with the `` characters, which I copied from another script.

Can anyone tell me why this is, and how I can insert these characters from my keyboard, which only has normal quote and double-quote characters?

Cheers and many thanks!

---

### Post by dcstar on 2010-10-26
> **wurlyfan said:**
> 
..........
Can anyone tell me why this is, and how I can insert these characters from my keyboard, which only has normal quote and double-quote characters?


The **`** is the top LHS key on my keyboard (next to "1").

---

### Post by andrew.46 on 2010-10-26
Hi wurlyfan,

> **wurlyfan said:**
> This script seems to work only if a surround the command with the `` characters, which I copied from another script.

Can anyone tell me why this is, and how I can insert these characters from my keyboard, which only has normal quote and double-quote characters

Many people dislike backtics and advocate something like the following:

```

andrew@skamandros~$ test=$(date)
andrew@skamandros~$ echo $test
Tue Oct 26 20:05:53 EST 2010

```

Andrew

---

### Post by wurlyfan on 2010-10-26
Thanks, I must need new spectacles :)

---

### Post by tornadof3 on 2010-10-26
Now you've found the backticks, perhaps you'd like to know why they're useful? The bash script is running the command line program "date", which runs, returns the current date in a long format and then exits. Your bash script captures the output of the date program and assigns it to your variable. You can do the same and capture the output of any command line program using back ticks, which is helpful if you're writing a script and would benefit from the functionality of a CLI program you know already exists and don't want to reinvent the wheel.

---

### Post by lavinog on 2010-10-26
Like what andrew said, using $() is typically better than backticks because it is easier to read (many users do not see the difference between ` and ' on some fonts), and provides nested commands:
```

$(command $(command))

```

Some people still prefer backticks because it is three less keystrokes.

---

