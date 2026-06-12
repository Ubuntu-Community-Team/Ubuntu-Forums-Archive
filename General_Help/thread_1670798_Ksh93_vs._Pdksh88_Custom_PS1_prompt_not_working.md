---
title: "Ksh93 vs. Pdksh88: Custom PS1 prompt not working"
date: 2011-01-19
forum: General Help
---

### Post by kristo5747 on 2011-01-19
Greetings! 

I have to work with a NFS user id between two hosts: A running Ksh 93 and B running pdksh 88.

My problem has to do with the custom prompt I created on A: it works like a charm and display colors:

 ```
   PS1="$'\E[46;31m'`logname`@$'\E[1;33m'`hostname -s`:$'\E[0m>"
```

But I switch over to B, it all goes to hell (private info removed). The prompt fails to display colors like host A ; instead, the color codes are displayed "in clear".

 ```
   $'\E[46;31m'NFS_user_name@$'\E[1;33m'host_name_for_B:$'\E[0m>
```

The prompt on host B is not displaying colors like host A so I want B to display a basic prompt instead. To get around the problem, I edited my .kshrc file to add this code at the end

```
    export NODE=`uname -n`
    
    case $NODE in
        host_name_for_B)
            PS1="[`logname`@`uname -n`]>"
            ;;
        *)
            PS1="$'\E[46;31m'`logname`@$'\E[1;33m'`hostname -s`:$'\E[0m>"
            ;;
    esac
```

The case statement does not work: PS1 does not switch to `PS1="[`logname`@`uname -n`]>"`. 

Any idea what could be the problem? Thanks!

---

