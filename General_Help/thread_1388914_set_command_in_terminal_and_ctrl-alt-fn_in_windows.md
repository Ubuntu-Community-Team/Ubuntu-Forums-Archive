---
title: "set command in terminal and ctrl-alt-fn in windows"
date: 2010-01-23
forum: General Help
---

### Post by Agilo on 2010-01-23
First Question: when I type set (without options) in the terminal, instead of getting the shell variables and their values, I get a very long code ending with:

> ri_get_methods () 
{ 
    local regex;
    if [ "$ri_version" = integrated ]; then
        if [ -z "$separator" ]; then
            regex="(Instance|Class)";
        else
            if [ "$separator" = "#" ]; then
                regex=Instance;
            else
                regex=Class;
            fi;
        fi;
        COMPREPLY=(${COMPREPLY[@]} "$( ri ${classes[@]} 2>/dev/null | 	      ruby -ane 'if /^'"$regex"' methods:/.../^------------------|^$/ and \
	      /^ / then print $_.split(/, |,$/).grep(/^[^\[]*$/).join("\n"); \
	      end' | sort -u )");
    else
        COMPREPLY=(${COMPREPLY[@]} "$( ruby -W0 $ri_path ${classes[@]} | ruby -ane 'if /^-/.../^-/ and \
	      ! /^-/ and ! /^ +(class|module): / then \
	      print $_.split(/, |,$| +/).grep(/^[^\[]*$/).join("\n"); \
	      end' | sort -u )");
    fi;
    COMPREPLY=($( compgen $prefix -W '${COMPREPLY[@]}' -- $method ))
}

Second question: Although this is not so much related to ubuntu, but does anyone know why windows doesn't give you multiple terminals from it's command prompt when I use ctrl-alt-fn (n=1...6) like ubuntu does?

Thanks for any help.

---

### Post by dcstar on 2010-01-23
> **Agilo said:**
> 
..........
Second question: Although this is not so much related to ubuntu, but does anyone know why windows doesn't give you multiple terminals from it's command prompt when I use ctrl-alt-fn (n=1...6) like ubuntu does?


Because Unix/Linux has done that from its initial existence because it was always a multi-user platform based on TTYs (serial TeleTYpe terminals), whereas DOS/Windows was a single user platform based on one local terminal.

---

### Post by DaithiF on 2010-01-24
for your first question on set, see [http://ubuntuforums.org/showthread.php?t=1378989](http://ubuntuforums.org/showthread.php?t=1378989)

---

### Post by Agilo on 2010-01-24
Thank you so much.

---

