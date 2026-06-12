---
title: "Shell Scripting Directories Navigation"
date: 2010-09-02
forum: General Help
---

### Post by Kinildson Persegueiro on 2010-09-02
Hi there!

    In DOS you can write in a .bat file the command...

```
cd C:\parent\child
```... then execute the file and the navigation works fine...

I couldn`t do the same in Ubuntu yet. Here is what I did...

I created a file myfile.sh

Here is the contents
```

#!/bin/bash
cd /home/mydirectorie/One/Two

```then...

```
chmod +x myfile.sh
```to make it executable.

And I`ve set the PATH variable including the dot...

```
PATH=.:pathalreadythere:another
```But when I run...

```
bash myfile.sh
```nothing happens, the directorie navigation does not work!
Please help!
Thanks! :D

---

### Post by Barrucadu on 2010-09-02
That's because when you run the shell script, another instance of bash is spawned which runs the script, exits, and then returns control to the 'main' bash instance. This is so that (amongst other things), you can execute shell scripts without needing to run them from a shell, and so that the main shell is not affected.

If you want to do that, you'll need to run it like this: `source /path/to/file`, which runs the script with the current bash instance (effectively it's the same as you just typing the commands yourself.)

---

### Post by limestone on 2010-09-02
you run the file with:
./file.sh

---

### Post by Kinildson Persegueiro on 2010-09-02
Thank you all guys...

source my/path/myfile.sh solved it!

---

### Post by Kinildson Persegueiro on 2010-09-04
.

---

### Post by Kinildson Persegueiro on 2010-09-07
.

---

