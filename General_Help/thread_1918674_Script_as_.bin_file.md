---
title: "Script as *.bin file?"
date: 2012-02-01
forum: General Help
---

### Post by nathatanu0 on 2012-02-01
I wanted to make a .bin file which will copy all the files with name having "am" in common... usually in the terminal we use "cp *am* "... I wrote the same command inside the .bin file, a shown below... but it acts like "echo"... please help.

file name "copier.bin"
------------------------------------
cp *am* /home/vmefiles/
-----------------------------------
then I did "chmod +x copier.bin
and finally "./copier.bin" but the out put is just:
 "cp *am* /home/vmefiles/"

please help...

---

### Post by oldos2er on 2012-02-01
Post moved to its own thread. Please start a new thread rather than hijacking someone else's.

---

### Post by Khayyam on 2012-02-03
nathantanu0 ..

You need to provide the script with the name of the interpreter with  which the commands are to be executed .. after all this isn't DOS .. heh

```
#!/bin/bash

echo "Who's a pretty boy then?"
```

```
chmod u+x prettyboy.bin
./prettyboy.bin
Who's a pretty boy then?
```

The suffix (.bin, .sh, etc) is un-necessary, 'prettyboy.bin',  'prettyboy.sh', or simply 'prettyboy' will all work, *.suffix is meerly a  convention used to make the scripting language the script is written in  identifiable in the filename. It is the "hash bang" and 'execuable' bit that does the  magic.

```
#!/bin/bash
# myscript
# comments are protected by a "#"

cp *am* /home/vmefiles/
```

.. but how about a 'test' condition (amazingly, there may not be any  files matching that expression in the directory), and 'mv' rather than  'cp', after all the script will copy these same files again the next  time the script is run. 

```
#!/bin/bash

if [[ -f *am* ]]; then
    mv *am* /home/vmfiles
fi
```

As for the interpreter, '#!/usr/bin/python' would run the content of the  script using the python interpreter, '#!/usr/bin/ruby' via ruby .. etc.

HTH ...

---

