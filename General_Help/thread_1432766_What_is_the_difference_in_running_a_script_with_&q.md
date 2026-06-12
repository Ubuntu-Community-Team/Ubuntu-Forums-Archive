---
title: "What is the difference in running a script with &quot;sh&quot;  &quot;./&quot;  &quot;.&quot; or &quot;source&quot; ?"
date: 2010-03-18
forum: General Help
---

### Post by xx007 on 2010-03-18
I'm learning Ubuntu from the book and I couldn't understand the difference between methods the book used to run scripts. for example :

./myscript.sh
sh myscript
. myscript
source myscript

it's really confusing for me that variables which defined in 'myscript.sh'
after running it with . or source remains in the shell variables (I mean you can see them in the "set" list) but it doesn't remain with sh or ./ ! it seems that for sh and ./ , variables are local. and at last which method Ubuntu use for executing profile and bashrc ?

thanks in advance

---

### Post by mcduck on 2010-03-18
"./" is just the generic way of executing any executable file from current directory. Tis is what I walways do, as it works for any executable binary files, and any shell scripts that are correctly formed (as in having the shebang to tell what shell they should be executed with).

"sh" runs the script with the default system shell (/bin/sh) regardless of what shell the script was made for. 
Kind of liek if you runa command like "gedit somefile.txt" to tell the system to open the file with gedit.

"source" (and ".") runs the command in the current shell session, instead of opening a new one like usually. Not really required for executing any normal scripts, mainly for running profile and setting scripts like ~/.bashrc and such.

edit:
If you want to define variable sin your own scripts you should export the variable, to make it a environment variable instead of local one. While sourcing the script would make that variable available in your current shell and it's child processes, exporting it makes it available in all your shells.
```
export VARIABLE=some_value
```

(in other words, if you open two terminal windows, *term1* and *term2*, and set a variable in *term*2 it's only available in that terminal, and any terminal you open from *term2*. If you export the variable it will be available in *term1* as well.)

---

### Post by slakkie on 2010-03-18
> **mcduck said:**
> "source" (and ".") runs the command in the current shell session, instead of opening a new one like usually. Not really required for executing any normal scripts, mainly for running profile and setting scripts like ~/.bashrc and such.


Think of sourcing files as including them. You can make several functions in file A, B and C, and then have several other scripts make use of those functions (and/or variables) by sourcing them.

eg:

```

#!/usr/bin/env bash
## file A

echo_file_a() {
  echo "file A"
}

```

```

#!/usr/bin/env bash
## Some file

. /path/to/file_a.sh
echo_file_a

```

---

### Post by xx007 on 2010-03-18
> **mcduck said:**
> 
(in other words, if you open two terminal windows, *term1* and *term2*, and set a variable in *term*2 it's only available in that terminal, and any terminal you open from *term2*. If you export the variable it will be available in *term1* as well.)

thanks for reply mcduck but your last paragraph doesn't work for me.

Well i test this :

create a bash named b.sh :
```
yo=14;export yo;
```
give it an execute permission.
and then run it in these ways:
```
./b.sh
sh b.sh
```
and then try to get yo value by echo $yo and still I couldn't get the value.

---

### Post by -grubby on 2010-03-18
Try running it as:

```

source b.sh

```

---

### Post by Slim Odds on 2010-03-18
I'd highly recommend the advanced bash scripting guide.

[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Also, the man page is good too.

---

### Post by xx007 on 2010-03-18
Thank you slim odds, It seems a good reference.

---

