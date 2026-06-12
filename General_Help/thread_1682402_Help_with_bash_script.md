---
title: "Help with bash script"
date: 2011-02-05
forum: General Help
---

### Post by ghostzen on 2011-02-05
Hi all,
I am trying a simple script to replace the command "which".  I am curious of how, for example,
```

$which rm *
/bin/r/
/usr/bin/perldoc

```


I write this script:    

```


#!/bin/sh

echo "$1"
cmd="$1"
IFS=:
for cmd in $PATH
        do
        echo $cmd
        
        done

```

This doesn't look right so I changed to:

```


#!/bin/sh

echo "$1"
cmd="$1"
for x in $PATH
        do
        if [ ! -d "$x/$cmd" -a -x "$x/$cmd" ]
        then
        echo $x/$cmd
        fi
        done

```
What did I do wrong? 
Please suggest
thanks

---

### Post by AlphaLexman on 2011-02-05
You cannot **echo** a command to get it to **execute**.

---

### Post by ghostzen on 2011-02-05
Hi Alpha,
I thought 
```

for x in $PATH
        do
        if [ ! -d "$x/$cmd" -a -x "$x/$cmd" ]
        then
        echo $x/$cmd
        fi
        done

```
would put my parameter in the $PATH and spit out only if it met my condition?

---

### Post by AlphaLexman on 2011-02-06
Your intentions are vague and confusing, but let me try to guess... You want to test your $PATH to see if $1 exists, if not, add it?

```
function pathmunge ()
{
	case ":${PATH}:" in
		*:"$1":*)	;;
		*)
			if [ "$2" = "after" ] ; then
				PATH=$PATH:$1
			else
				PATH=$1:$PATH
			fi
	esac
}

```
...And it's usage is this:
```
pathmunge /path/to/directory [after]
```

---

### Post by ghostzen on 2011-02-06
Sorry for the confusion, but ultimately I want my script to work like this:
```

$sh test.sh grep
/bin/grep

and

$sh test.sh grep bash
/bin/grep
/bash/bash


```


This is what I have got so far:
```

#!/bin/sh
#test.sh

FINDALL=FALSE

case $PATH in

:*)
    PATH=".:$PATH"
    ;;
*::*)
    PATH=`echo $PATH | sed -e 's/::/:.:/g'`
    ;;
*:)
    PATH="$PATH:."
    ;;

esac


cmd="$*"

IFS=$OLDIFS
IFS=:
set -- $PATH 
IFS=$OLDIFS


case $cmd in
*/*)
    echo $cmd
    ;;
-a)
  echo "$1"
  shift
        for xpath in $PATH
                 do
                  if [ ! -d "$xpath/$cmd" -a -x "$xpath/$cmd" ]
                        then
                        FOUND=true
                        echo $xpath/$cmd
                      continue
                  fi
        done

                  if [ "$FOUND" = false ]
                        then
                        echo "$cmd not in search path"
                  fi
        ;;


*)
   FOUND=false
      for xpath
          do
            if [ ! -d "$xpath/$cmd" -a -x "$xpath/$cmd" ]
                  then
                  FOUND=true
                  echo $xpath/$cmd
                  break
                fi
                done
            if [ "$FOUND" = false ]
                  then
                  echo "$cmd not in search path"
            fi
;;

esac


```
my script only loop the 1st variable such as 
$sh test.sh grep,  but if I put
```

$sh test.sh grep bash

```
I get nothing???
I am still scratching my head over this.

---

### Post by AlphaLexman on 2011-02-06
Forget the script code for now, what is your goal?

Are you testing to see if a command exists in your $PATH or are you trying to add an executable (non-directory) to your $PATH [wrong!]

EDIT: maybe this will help,
```
if [[ -x `which $1 2>/dev/null` ]]; then
    echo "True"
else
    echo "False"
fi
```

---

### Post by ghostzen on 2011-02-06
Hi Alpha,
My goal is to write a script that replaces the built-in "which".  

I am learning bash script through books and online sources, and this is one of the challenges I am giving myself.  
Btw, I got the solution working :).  If you're interested, then I'll post my script.

thanks
Tam

---

