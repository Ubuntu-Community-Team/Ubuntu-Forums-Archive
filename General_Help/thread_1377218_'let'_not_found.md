---
title: "'let' not found"
date: 2010-01-10
forum: General Help
---

### Post by ankit.vader on 2010-01-10
I am a linux newbie, and recently started shell programming. whenever I use 'let' command it gives me an error 'command not found'. I am using ubuntu 9.10 with bash.

please help...

---

### Post by Brandon Williams on 2010-01-10
The command 'let' is a bash builtin, so if you're using it in a script that runs /bin/sh, it will fail, since /bin/sh on Ubuntu is dash, not bash.

If that doesn't help, there may be some shell constructs that you could use where bash would attempt to run let as an external command. Gives us some more specifics about how you're using it, and we might be able to suggest an alternative.

---

### Post by NoaHall on 2010-01-10
```

#! /bin/bash

```
At the top of your script :)

---

### Post by Dark Angel on 2010-03-12
It's because Ubuntu uses the dash shell as default and doesn't always recognize when you try to set the shell in a script.  Even if you enter "echo $SHELL" into the console it will tell you you're using /bin/bash but for some reason it's actually using dash instead.

use:
sudo dpkg-reconfigure dash
<password>

and when you get the option select "no" to actually use bash instead of dash

---

### Post by deuson on 2010-05-02
Thanks for Dark Angel,i also have this problem and what you say can  solve it  perfectly.

---

### Post by Light-kun on 2010-11-20
Thanks, /bin/bash helped =)

---

