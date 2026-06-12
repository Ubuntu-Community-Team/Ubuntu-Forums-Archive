---
title: "Calling apt-get with python!"
date: 2010-08-29
forum: General Help
---

### Post by cgroza on 2010-08-29
Hello, I am trying to make a python program that takes the user input and and puts it after "sudo apt-get install (userinput). So far it seems it works but it seems it runs only sudo apt-get install (without user input). The code looks like this right now!

```
#!/usr/bin/env python

import os

print('Welcome to my AppInstaller.')
a = raw_input('Enter app name from repository: ')
os.system('sudo apt-get install '),a
raw_input('Press enter to continue.')

```

I would like to know how to make the program run sudo apt-get install + user input, not just sudo apt-get install!

Thanks!

---

### Post by oldfred on 2010-08-29
Something like this:

cmd="sudo apt-get install " + a
 os.system(cmd)

---

### Post by Dies on 2010-08-29
I don't see how you expect this work.
```
os.system('sudo apt-get install '),a
```

Kind of surprised it doesn't cause a syntax error.

---

### Post by cgroza on 2010-08-29
> **Dies said:**
> I don't see how you expect this work.
```
os.system('sudo apt-get install '),a
```Kind of surprised it doesn't cause a syntax error.
I just folowed some tutorials on youtube. I know python for 1 day!

---

### Post by cgroza on 2010-08-29
Thanks [oldfred]("http://ubuntuforums.org/member.php?u=852711")! You helped me out a lot.

---

### Post by Dies on 2010-08-29
> **cgroza said:**
> I just folowed some tutorials on youtube. I know python for 1 day!

I didn't mean anything by it.

You already had an answer when I posted. ;)

---

### Post by cgroza on 2010-08-29
> **Dies said:**
> I didn't mean anything by it.

You already had an answer when I posted. ;)

No problem, you were helpful to me also.

---

