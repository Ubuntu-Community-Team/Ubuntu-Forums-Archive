---
title: "does any one have reason for this ?"
date: 2011-06-04
forum: General Help
---

### Post by raja.genupula on 2011-06-04
Hello Friends 
                    I dont know , why i did this . i have open my terminal and just typed simply " yes " 
then i got a flow of "y" . its floating in the terminal . ctrl+z help me to stop that , but i dont know whats the reason behind that , i am eager to know about . 
                                                                     thank you in advance .

---

### Post by IWantFroyo on 2011-06-04
Tried it. Interesting. I didn't know that.It's probably a developer joke. "apt-get moo" does something similar, and I've read that in the past, there were similar jokes that were removed.
You might want to read this:
[http://en.wikipedia.org/wiki/Easter_egg_(media](http://en.wikipedia.org/wiki/Easter_egg_(media))

---

### Post by Toz on 2011-06-04
```
man yes
```

You can use this in bash scripts to answer yes to commands that wait for a y to continue.

---

### Post by matt_symes on 2011-06-04
Hi

It's no Easter egg and can be useful.

It can be piped into any command that may require 'yes' as confirmation.

Here's a contrived example (as rm has the force option)
```

matthew@matthew-laptop:~/a$ ls -l
total 0
-r--r--r-- 1 matthew matthew 0 2011-06-04 02:22 a
-r--r--r-- 1 matthew matthew 0 2011-06-04 02:22 b
-r--r--r-- 1 matthew matthew 0 2011-06-04 02:22 c
matthew@matthew-laptop:~/a$ rm a
rm: remove write-protected regular empty file `a'? n
matthew@matthew-laptop:~/a$ yes | rm a
matthew@matthew-laptop:~/a$ ls -l
total 0
-r--r--r-- 1 matthew matthew 0 2011-06-04 02:22 b
-r--r--r-- 1 matthew matthew 0 2011-06-04 02:22 c
matthew@matthew-laptop:~/a$ 
```

Kind regards

---

### Post by m_duck on 2011-06-04
It should also be noted that ctrl+z will simply background the process, so it will still be running (type in ***fg*** and you will see its continued output). Ctrl+c would be the combination to kill it.

---

### Post by raja.genupula on 2011-06-04
Thank you guys

---

