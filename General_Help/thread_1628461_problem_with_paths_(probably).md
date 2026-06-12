---
title: "problem with paths (probably)"
date: 2010-11-22
forum: General Help
---

### Post by tobytoby on 2010-11-22
Hi, I get 'No such file or directory' when I try to run a python script from an application launcher. I do not get the error msg when running it from terminal which means I guess it has something todo with how I write the paths.

This is how I have done it:

```
#!/usr/bin/python

import os

os.chdir('C:/home/user/script/')
f = open('time.txt', 'r+')
```

I have also tried to write f=open('c:/home/user/script/time.txt') resulting in the same error msg.

What is the correct way to write the path in this app?

Thanks.

---

### Post by lukeiamyourfather on 2010-11-22
What does this say when you run it?

```
#!/usr/bin/python

import os

filePath = 'C:/home/user/script/time.txt'

if os.path.isfile(filePath):
    print '%s is a file' % (filePath)
else:
    print '%s is not a file' % (filePath)

```

For Python 3.X...

```
#!/usr/bin/python

import os

filePath = 'C:/home/user/script/time.txt'

if os.path.isfile(filePath):
    print('%s is a file' % (filePath))
else:
    print('%s is not a file' % (filePath))

```

---

### Post by tobytoby on 2010-11-22
when run from terminal I get
C:/home/user/script/time.txt is not a file

---

### Post by lukeiamyourfather on 2010-11-23
> **tobytoby said:**
> when run from terminal I get
C:/home/user/script/time.txt is not a file

You're sure the file is there? If so then it might be a permission thing. I don't do much Python on Windows so not sure.

---

### Post by tobytoby on 2010-11-23
I have solved it now by using (not so elegant) absolute paths.

---

