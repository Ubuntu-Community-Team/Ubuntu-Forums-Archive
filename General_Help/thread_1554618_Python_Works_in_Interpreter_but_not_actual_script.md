---
title: "Python Works in Interpreter but not actual script"
date: 2010-08-17
forum: General Help
---

### Post by pippin418 on 2010-08-17
I wrote a script to use egrep to search files for '#!/usr/bin/python' so I could tell what my Python scripts were/where they were. It grabs 'ls' and separates it into an array. It uses ls -F so I can pop anything with a / in it; giving me just files. It then egrep's them. Here's the code.

```
#!/usr/bin/python
import commands as com
ls = com.getoutput("ls -F")
ls = ls.split("\n")
for value in ls:
    if "/" in value:
        z = ls.index(value)
        ls.pop(z)

a = 0
b = 1
c = len(ls)
e = '#!/usr/bin/python'
#while a < c:
#    z = str(ls[a:b]).replace("[", "").replace("]", "").replace("*", "").replace("]", "").replace("[", "")
#    l = "egrep '%s' %s" % (e, z)
#    print com.getoutput(l), " at %s" % z
#    a = a + 1
#    b = b + 1

while a < c:
    z = str(ls[a:b]).replace("[", "").replace("]", "").replace("*", "").replace("]", "").replace("[", "")
    l = "egrep '%s' %s" % (e, z)
    if com.getoutput(l) not in "egrep:":
        print com.getoutput(l), " at %s" % z
    else:
        pass
    a = a + 1
    b = b + 1

```When I run all that code in the interpreter, it works. If I run it from Bash (eg ./egrep) it throws me an error like this 'egrep: [Screenshot.png]: No such file or directory' for every file in the directory. Any ideas? Also, it doesn't filter out the directories either.

---

### Post by DaithiF on 2010-08-17
Hi,
I'm not sure why you're writing a script, ie. why not just:
```
grep '#!/usr/bin/python' *

```but assuming you're doing it for a good reason, e.g. as a learning exercise then I would point out a number of problems:
> 
```

import commands as com
ls = com.getoutput("ls -F")
ls = ls.split("\n")
for value in ls:
       if "/" in value:
             z = ls.index(value)
             ls.pop(z)

```1. why parse an external command when you can use an inbuilt function instead: os.listdir()

2. the reason directories are not removed is that your code changes the length of the ls list while you are iterating through it.  this means that you skip certain entries.  To illustrate, imagine you have this list:
```
animals = [ 'dog', 'cat', 'bird' ]
for value in animals:
   print value
   if value == 'cat':
      animals.pop(animals.index(value))
```what gets printed?  what happened to the 'bird' entry?  by removing an item from the loop, and shortening its length from 3 to 2, the forloop thinks it is done after it has done its 2nd element.  So for every directory your code pops from the list, you will skip some entry, which could be a file or a directory, depending on the order of the output from ls.

instead of all this, do:
```
import os
files = [ f for f in os.listdir('.') if os.path.isfile(f) ]

```
> ```
    z = str(ls[a:b]).replace("[", "").replace("]", "").replace("*", "").replace("]", "").replace("[", "")
```This is awful, just awful :)   You're taking a slice of your list, converting it to a string, then stripping off the list brackets from that???  Why?  You've already shown previously that you know how to iterate over a list -- why not just do that here too?
```
for z in ls:

```> if com.getoutput(l) not in "egrep:":
    print com.getoutput(l), " at %s" % z

You're running the command twice, once to get the results, and again to print them out?  run the command ONCE, capture its output in a variable and use that variable however many times you need.
```
output = com.getoutput(l)

```As to the error message you were getting, my guess is that code you ran to give those messages isn't the same code you posted here.  in that version you hadn't successfully stripped the [ ] brackets around your filenames.

in any case, heres a slightly better version:
```
import os
import commands as com

e = '#!/usr/bin/python'

files = [ f for f in os.listdir('.') if os.path.isfile(f) ]

for file in files:
    output = com.getoutput("egrep '%s' '%s'" % (e, file))
    if output:
        print "Found match '%s' in file %s" % (output, file)

```

---

### Post by ziekfiguur on 2010-08-17
Also, the python documentation says:
> 
The subprocess module provides more powerful facilities for spawning new processes and retrieving their results. Using the subprocess module is preferable to using the commands module.


i would suggest using something like:
```

#!/usr/bin/env python
import subprocess
proc = subprocess.Popen(['ls', '-F'], stdout=subprocess.PIPE)
ls = []
for line in proc.stdout:
    if '/' not in line:
        ls.append(line)
proc.wait() # dont let it go zombie

```

---

### Post by pippin418 on 2010-08-18
I wasn't going for efficiency in the script. I was trying to figure out why 
egrep '#!/usr/bin/python' *
didn't work. I feel like it's being recursive, even though it's not. It doesn't work unless I do it like the script I have above. Yes, if I had tried to go for efficiency I probably wouldn't waste so much memory. You did destroy my script and made it a tiny one. The original worked after I used it in a new terminal. Still works. I'll use your's though. Learned a bit from it.

Thanks

--EDIT--
ls -F outputs *'s and /'s so part of that was to get rid of those.
 z = str(ls[a:b]).replace("[", "").replace("]", "").replace("*", "").replace("]", "").replace("[", "")

--EDIT.. 2--
Fine. When I run grep '#!/usr/bin/python' * any other time it doesn't work, but now it does. Well, there goes a script.

---

### Post by DaithiF on 2010-08-18
> **pippin418 said:**
> I was trying to figure out why 
egrep '#!/usr/bin/python' *
didn't work. 

that will work. perhaps you were trying:
```
egrep "#!/usr/bin/python" *

```
the '!' character in bash is the history expansion character, bash tries to find a command in your history which matches what follows the '!' character, and expands that part of your command with that full command from your history, or a message like 'event not found' if there is no matching command in your history.

so when I run this command:
```
$ egrep "#!/usr/bin/python" *
```
i get:
```
bash: !/usr/bin/python": event not found

```

To prevent this, either enclose in single quotes, or escape the ! if using double quotes:
```
egrep '#!/usr/bin/python' *
egrep "#\!/usr/bin/python" *

```

---

### Post by pippin418 on 2010-08-21
I think I was using single quotes, since I know ! produces an error.

But it works now, so no worries.

---

