---
title: "Custom Terminal Command to Launch Python Script"
date: 2011-04-19
forum: General Help
---

### Post by RadiusD on 2011-04-19
Hello, Noob here. I have written a little python script and I was wondering how you make a custom command to launch the script. 

So instead of typing

>> python myscript.py 

into command line
all I have to do is type

>> myscript

and it launches my python program. 

How can this be done? Any help is appreciated. Thank You

---

### Post by ~Plue on 2011-04-19
you could use an alias in your ~/.bashrc (or /etc/bash.bashrc if you want to make it available system wide)
```
alias myscript='python /path/to/myscript.py'
```

---

### Post by sanderd17 on 2011-04-19
you can make a bash script for that. Type
```

#! /bin/bash
python myscript.py

```

in a file myscript
then give it execute rights
```

chmod 755 myscript

```
and you can execute it with
```

./myscript

```

If you want to get rid of the "./", you will need to place the file in a directory of your PATH, execute
```

$PATH

```
to see what directories that are in your path and do
```

export PATH=$PATH:/home/user/bin/

```
to add a specific directory to your path

---

### Post by junapp on 2011-04-19
learn about "shebang"
[http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))


from:
[http://ubuntuforums.org/archive/index.php/t-316290.html](http://ubuntuforums.org/archive/index.php/t-316290.html)

> 
UbuWu
December 10th, 2006, 02:36 PM
If you add the following line to the start of the program:

#! /usr/bin/env python

And then make the file executable (chmod +x filename)

You can run the program by just typing its name. It doesn't need to have the .py extension.



---

### Post by RadiusD on 2011-04-19
Thanks for everyones help! I got it working with ~Plue's solution

> **~Plue said:**
> you could use an alias in your ~/.bashrc (or /etc/bash.bashrc if you want to make it available system wide)
```
alias myscript='python /path/to/myscript.py'
```

I had to also reload bash using
>> exec bash

and after that it worked perfectly. 

Thanks All! This is an awesome little trick to know.

---

