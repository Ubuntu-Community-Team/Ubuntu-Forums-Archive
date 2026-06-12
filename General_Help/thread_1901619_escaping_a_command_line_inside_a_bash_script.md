---
title: "escaping a command line inside a bash script"
date: 2011-12-28
forum: General Help
---

### Post by kwyto on 2011-12-28
hi, 

i need to add a configuration to my tomcat for JAVA_OPTS

JAVA_OPTS="
-Ddateformat=yyyy-MM-dd HH:mm:ss
"

my problem is that when tomcat starts it believes that HH:mm:ss is another command. I need to keep the space between dd and HH. I don't know much about bash script so any help is greatly appreciated.

---

### Post by zero2xiii on 2011-12-29
Easy,

```
JAVA_OPTS="
 -Ddateformat=yyyy-MM-dd\ HH:mm:ss
 "
```

or MAYBE

```
JAVA_OPTS="
 -Ddateformat=yyyy-MM-dd%20HH:mm:ss
 "
```

Cherz

---

### Post by kwyto on 2011-12-29
didn't work. i had tried the first one already before posting. for the second one it uses %20 as part of the string showing yyyy-MM-dd%20HH:mm:ss 
thank you for giving it a shot.

---

### Post by kalfusisagod on 2011-12-29
Try single quoting whatever you're trying to escape. I think the only things passed single quoted are variables like $HOME.

---

### Post by nothingspecial on 2011-12-29
> **kalfusisagod said:**
> Try single quoting whatever you're trying to escape. I think the only things passed single quoted are variables like $HOME.

You have that back to front

> 3.1.2.2 Single Quotes

Enclosing characters in single quotes (‘'’) preserves the literal value of each character within the quotes. A single quote may not occur between single quotes, even when preceded by a backslash. 

> Enclosing characters in double quotes (‘"’) preserves the literal value of all characters within the quotes, with the exception of ‘$’, ‘`’, ‘\’, and, when history expansion is enabled, ‘!’. The characters ‘$’ and ‘`’ retain their special meaning within double quotes (see Shell Expansions). The backslash retains its special meaning only when followed by one of the following characters: ‘$’, ‘`’, ‘"’, ‘\’, or newline. Within double quotes, backslashes that are followed by one of these characters are removed. Backslashes preceding characters without a special meaning are left unmodified. A double quote may be quoted within double quotes by preceding it with a backslash. If enabled, history expansion will be performed unless an ‘!’ appearing in double quotes is escaped using a backslash. The backslash preceding the ‘!’ is not removed.

The special parameters ‘*’ and ‘@’ have special meaning when in double quotes (see Shell Parameter Expansion). 

---

### Post by kwyto on 2011-12-29
Thank you all for your replies. I have decided to go on a different route. I tried pretty much all the combinations, except for the one that works :) The problem arises because of all the layers tomcat uses for its scripts. JAVA_OPTS is set inside setenv.sh which is set in a variable inside catalina.sh, which then is put into another variable inside stop, start, debug and shutdown scripts. At that point it doesn't matter if I figured it out, it is just good design to stay away from all that mess. I'm going the programmatically way, just because it will be easier to manipulate if I decide to change the pattern in the future.

---

