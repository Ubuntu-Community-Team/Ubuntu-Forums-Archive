---
title: "bash - how to define an error handler"
date: 2010-09-29
forum: General Help
---

### Post by HamletDRC on 2010-09-29
pretty new to bash scripting here. this is a beginner question. 

I want to define a simple error handler for a script. 

Image a script that does a few commands: 
```

ls .
cd ..
touch ... 

```
whatever, it doesn't matter. 

I want to define one error handler for the script, so if any of the steps error than the script is terminated and the error handler is run. 

I see the -e option to quit on errors, but I want a GOTO on errors. 

Thanks in advance,

---

### Post by amauk on 2010-09-29
This assumes commands exit 0 on success
Any other value is an error
(this is true for 99% of programs, but you may find the odd one doesn't follow this)

```
function try_cmd
{
    if [ -n "$1" ]; then
        eval "$1"

        if [ "$?" -ne 0 ]; then
            error_handler "$1"
        fi
    fi
}

function error_handler
{
    echo "Error in cmd \"$1\""
    exit 1
}

try_cmd 'cd /'
try_cmd 'ls -l'
try_cmd 'touch foo'
try_cmd 'i_dont_exist --foo=bar'
```

---

