---
title: "echo -e in scripts doesn't seem to work well?"
date: 2009-10-08
forum: General Help
---

### Post by Sarteck on 2009-10-08
I have a script, tuning-primer.sh, which I've used on our old CentOS server with no real problem at all.  However, it's all screwy on our Ubuntu server.
```

-e \e[0m-e
-e \e[0m-e \e[0m-e Using login values from ~/.my.cnf

-e \e[0m-e e[1;31mc
-e - INITIAL LOGIN ATTEMPT FAILED -

-e \e[0m-e \e[0m-e Testing for stored webmin passwords:-e \e[0m-e e[1;31mc
-e  None Found

-e \e[0m-e \e[0m-e Could not auto detect login info!

-e \e[0m-e \e[0m-e Found Sockets:
/var/run/mysqld/mysqld.sock

-e \e[0m-e e[31mc
-e Using: /var/run/mysqld/mysqld.sock
-e \e[0mWould you like to provide a different socket?: [y/N]

```

Now, the relevant part of the script is:```
cecho ()

## -- Function to easliy print colored text -- ##

                                # Color-echo.
                                # Argument $1 = message
                                # Argument $2 = color
{
export black='\e[0m\c'
export boldblack='\e[1;0m\c'
export red='\e[31m\c'
export boldred='\e[1;31m\c'
export green='\e[32m\c'
export boldgreen='\e[1;32m\c'
export yellow='\e[33m\c'
export boldyellow='\e[1;33m\c'
export blue='\e[34m\c'
export boldblue='\e[1;34m\c'
export magenta='\e[35m\c'
export boldmagenta='\e[1;35m\c'
export cyan='\e[36m\c'
export boldcyan='\e[1;36m\c'
export white='\e[37m\c'
export boldwhite='\e[1;37m\c'

local default_msg="No message passed."
                                # Doesn't really need to be a local variable.

message=${1:-$default_msg}      # Defaults to default message.
color=${2:-$black}              # Defaults to black, if not specified.

  echo -e "$color"
  echo -e "$message"
  tput sgr0                     # Reset to normal.
  echo -e "$black"
  return
}
```
Am I missing something here?

---

### Post by Tibuda on 2009-10-08
"echo -e" don't work in sh. bash supports it, but I'm not sure about other shells. Make sure your shebang is "#!/bin/bash" instead of "#!/bin/sh".

---

### Post by Sarteck on 2009-10-08
> **danielrmt said:**
> "echo -e" don't work in sh. bash supports it, but I'm not sure about other shells. Make sure your shebang is "#!/bin/bash" instead of "#!/bin/sh".

Huzzah!

I've googled and found answers similar to yours, but was still getting the same results.  I've been head-desking for quite a while, and then your post opened my eyes...

...I was doing **sh tuning-primer.sh** rather than **./tuning-primer.sh**  ! XD  So I'm guessing that must have "over-ridden" the shebang to use sh rather than bash.

I feel so dumb... but I hope this solves the problem for anyone else who's as much a dummy as me.  XP

---

