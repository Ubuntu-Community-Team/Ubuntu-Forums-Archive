---
title: "Passing arguments to a Bash script"
date: 2012-08-04
forum: General Help
---

### Post by Stonecold1995 on 2012-08-04
I'm making a Bash script, and I need to be able to pass arguments to it.  For example, let's say I have a script that starts out like this:

```
#!/bin/bash

VAR1="value 1"
VAR2="value 2"
VAR3="value 3"
```

I want to be able to use arguments to override one or more of the variables if I have to.  So I want to be able to use *./script.sh --var1 "alternate value 1"* or even *./script.sh --var3 "alternate value 3" --var1 "alternate value 1"*, etc without having to worry about the order.  There must be an easy way to do this, but I don't know it.  This is the most I can do right now:
```
#!/bin/bash

if [ "$1" != "" ]; then
   if [ "$1" = "--help" -o "$1" = "-h" ]; then
      echo -e "Command line options:\n\n      -h, --help    display this help\n"
      exit 0
   fi
   echo -e "\nInvalid arguments.  Use --help or -h for information about this script.\n"
   exit 1
fi
```

But I don't know how to put a value in there (such as "--help subject") or how to deal efficiently with many possible arguments (currently I'd have to have a lot of "if" operators checking for every possible combination of arguments, which obviously isn't practical).

---

### Post by spjackson on 2012-08-05
Dealing with complex command line arguments manually is tedious. The usual tools used to handle this situation are the bash builtin getopts, and the external getopt command.

[Here]("http://linuxwell.com/2011/07/14/getopt-in-bash/") and [here]("http://wiki.bash-hackers.org/howto/getopts_tutorial") are a couple of tutorials that explain how to use these. A little effort is required to understand these tools, but it is easier than trying to code a d-i-y solution.

---

