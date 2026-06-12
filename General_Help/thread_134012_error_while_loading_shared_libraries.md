---
title: "error while loading shared libraries"
date: 2006-02-21
forum: General Help
---

### Post by ninocass on 2006-02-21
Im trying to run windows communicator (linux version ;) )
[http://www.communicator.pl/download.html](http://www.communicator.pl/download.html)

im getting the following error:
```

Communicator: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory

```

the program comes with 2 folders bin and lib

in the programs folder is a proggy called start_a

which has:
```

#!/bin/bash
# runs Communicator
# created by InstallMade - www.installmade.com
ex=Communicator
ds=$HOME/Communicator/bin
cd $ds
dsl=$HOME/Communicator/lib
export LD_LIBRARY_PATH=$dsl:$LD_LIBRARY_PATH
export PATH=$PATH:$ds:$dsl
$ex

```

im guessing i done have the lib files in the right place?

could anyone advise me

Many thanks

Nino

---

### Post by suRoot on 2006-02-21
Looks like you just need to extract the communicator archive to /home/username/Communicator

The 'dsl' variable in that script (which points to $HOME/Communicator/lib) gets exported as part of the LD_LIBRARY_PATH, which is where the program will look for shared libs & such.

You can check your '$HOME' variable by typing the following in a console:

```
echo $HOME
```

Which ought to return something like /home/username

Then just make sure the path /home/username/Communicator/lib exists & it should work!

---

