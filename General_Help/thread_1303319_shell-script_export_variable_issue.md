---
title: "shell-script: export variable issue"
date: 2009-10-28
forum: General Help
---

### Post by Chily123 on 2009-10-28
When I manually export a variable from the shell, i am able to get the content back:

[I]me@pizza:~$ export my_var=123
me@pizza:~$ echo $my_var
123
me@pizza:~$ [/I]

Everything is fine.

Now i have those two little shell-scripts. First one (export_text_1.sh):

[I]#!/bin/bash
export some_var=value[/I]

Here is the second one (export_text_2.sh):

[I]#!/bin/bash
./export_text_1.sh
echo $some_var[/I]

Now when i call the second one, i receive this:

[I]me@pizza:~/tmp$ ./export_text_2.sh

me@pizza:~/tmp$[/I]

It looks like the variable some_var is not defined or empty. What am i doing wrong ?

---

### Post by yeats on 2009-10-28
Sounds like an issue of scope, meaning that the variable is assigned within the script and *stays* within the script.  As far as I understand it, a script is kind of like running an entirely different shell so variables assigned within it do not affect your "live" shell session.  

My experience with shell scripts is limited though... :-)

---

### Post by djurny on 2009-10-28
try running
```

. ./export_text_1.sh
./export_text_2.sh

```

the variable that is set in *export_text_1.sh* is 'global' for shell executing that particular script and its descendents only, it will not 'export' it to the calling shell..

by using '. ./export_text_1.sh' or 'source ./export_text_1.sh' you will execute the script in the context of the running shell, rather than starting a new shell interpreter to run your script.. that way the export is effective in the running shell as well..

check [http://www.ibm.com/developerworks/library/l-bash.html](http://www.ibm.com/developerworks/library/l-bash.html) for some more detail on environment variables and exporting them..

---

### Post by Chily123 on 2009-10-28
@chriss: Thx for the answer, but hmm... i don't think so, this runs without problem under fedora core 11.

edit: im wrong, this neither does work unter fc11.

---

### Post by Chily123 on 2009-10-28
@[djurny]("http://ubuntuforums.org/member.php?u=814491")

This works, but this is not the way i want it to use. The idea is to call only one shell-script calling another to set a variable. That way, the main script will get the variable.

---

### Post by djurny on 2009-10-28
i'm afraid that just won't work that way.. there is no way a spawned shell can set a variable in it's parent's environment.. (experts correct me if i'm wrong)..
usually the following is done to achieve the same:
```
#!/bin/bash
# test-1.sh
echo "abc"

```
```

#!/bin/bash
# test-2.sh
ABC=$(./test-1.sh)
echo ${ABC}

```

---

### Post by Chily123 on 2009-10-28
Oh yeah, nice way to do so, too bad my knowledge of scripting is so poor, thx.

---

