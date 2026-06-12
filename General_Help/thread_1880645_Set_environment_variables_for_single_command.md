---
title: "Set environment variables for single command"
date: 2011-11-14
forum: General Help
---

### Post by natomb on 2011-11-14
Hello,
 
 
I have searched the Internet for quite some time to assist me in solving following solution, yet proposed solutions do not work. Here is what I want to achieve:
 
Execute a program with custom environment variables that must be set for the invocation of the program only.
 
 
More precisely:
 
I want to invoke a program "myprog" that reads a number of environment variables. Those environment variables must not be set for any other purpose than running "myprog". Thus, setting the environment variables prior to running "myprog" and deleting them is not an option. Yet, there are plenty of environment variables and they are listed in a file.
 
 
Basically, I want to achieve:
 
bash -configure_with <file_with_environment_variables> -execute myprog
 
 
The "file_with_environment_variables" contains a list of environment variables, e.g. 
PATH=/mybin
TIME=now
TEXT=Hello
 
 
Thank you very much for your support, which I assume is very simple in Linux as everything else is - once you know about.
 
 
Bjoern

---

### Post by Lars Noodén on 2011-11-14
Something like this should work:

```

PATH=/mybin TIME=now TEXT=Hello *myprog*

```

Or, if your program is a shell script, you can set the variables inside the script itself.

---

### Post by dethorpe on 2011-11-14
You could create a wrapper script to source and export the file of env vars then run the program, that way they'ed only be set in the shell running the wrapper and the program:
 
you will have to add the export command to the vars in your file though, i.e make the lines:
  export PATH=/mybin

  
e.g. create a file called "run_myprog.sh" with this content
 
```
 
 #! /usr/bin/bash
 
. file_with_environment_variables.sh
myprog

```
 
make it executable and then run it
 
(you will need to add any file paths for the files on your system to the commands above)

---

### Post by Vaphell on 2011-11-14
will myprog see these envvars?

little test:
- env.txt
```
ENV_VAR1=abc
ENV_VAR2=def
```
- env_test.sh
```
#!/bin/bash

source ./env.txt

echo === $0 ===
echo ${ENV_VAR1}
echo ${ENV_VAR2}

[COLOR="Green"]./env_test2.sh[/COLOR]
[COLOR="Blue"]source ./env_test2.sh[/COLOR]
```
- env_test2.sh
```
#!/bin/bash

echo === $0 ===
echo ${ENV_VAR1}
echo ${ENV_VAR2}
```

output:
```
$ ./env_test.sh 
=== ./env_test.sh ===
abc
def
[COLOR="Green"]=== ./env_test2.sh ===[/COLOR]


[COLOR="Blue"]=== ./env_test.sh ===
abc
def[/COLOR]

```

(source and . are the same thing)

---

### Post by natomb on 2011-11-14
Thank you, this solves the thing.
 
I am always surprised how simple Linux is - once you know how to do it.

---

### Post by dethorpe on 2011-11-15
> **Vaphell said:**
> will myprog see these envvars?
 
little test:
- env.txt
```
ENV_VAR1=abc
ENV_VAR2=def
```
...
[COLOR=#008000]./env_test2.sh[/COLOR]
[COLOR=blue]source ./env_test2.sh[/COLOR]


 
Yup, sourceing the script from the wrapper works if you don't wan't to export the vars. It means that the script runs in the same shell as the wrapper rather than a new shell with its own environment which inherits the exported vars (which is why $0 stays unchanged in your examples). Any vars declared in the called script ([COLOR=#0000ff]env_test2.sh) [/COLOR]will then become available in the calling script ([COLOR=#0000ff]env_test.sh[/COLOR]), you may not want that if you are doing further work in the caller. e.g. called script could change the value of a var with the same name in the caller.

---

