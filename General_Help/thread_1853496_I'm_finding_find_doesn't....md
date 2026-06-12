---
title: "I'm finding find doesn't..."
date: 2011-10-02
forum: General Help
---

### Post by Kronalias on 2011-10-02
I'm having trouble using 'find'. Here's an example of the problem where I'm trying to find all the filenames that contain the text 'launchpad' in my current directory and those below it.

In a directory, say ~/test, make two subdirectories:
~/test/my-launchpad
~/test/other

Create a couple of text files whose names contain 'launchpad' in ~/test/other:
~/test/other/how-to-launchpad1.txt
~/test/other/how-to-launchpad2.txt

Now in ~/test search for anything containing 'launchpad', and the text files aren't found:
kronalias@lappy2:~/test$ find -name *launchpad*
./my-launchpad

If I remove the my-launchpad directory and repeat, then I get the expected result:
kronalias@lappy2:~/test$ find -name *launchpad*
./other/how-to-launchpad1.txt
./other/how-to-launchpad2.txt

What on earth am I doing wrong?

---

### Post by TeoBigusGeekus on 2011-10-02
Try with quotes:
```
find -name "*launchpad*"
```

---

### Post by Vaphell on 2011-10-02
you need to put your pattern in quotes
'*launchpad*'

if you don't do that, shell will expand it before passing it to find. If the dir exists, find will see -name my-launchpad and obviously files will fail the test, if expansion fails (there is nothing matching the pattern in current dir) the string will be passed literally and find sees unmodified pattern.

try```
echo *launchpad*
echo '*launchpad*'
``` to get the idea what happens

---

### Post by Kronalias on 2011-10-02
Problem solved - Thanks muchly to you both!

---

