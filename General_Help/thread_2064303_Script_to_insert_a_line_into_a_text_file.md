---
title: "Script to insert a line into a text file?"
date: 2012-09-28
forum: General Help
---

### Post by Stonecold1995 on 2012-09-28
How do I insert a line of text into a specific location in a text file?  I'm trying to write a script that installs itself and a few other scripts that run at startup.  I want to insert a line right above the "exit 0" in "/etc/rc.local" like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

/path/to/script1.sh &

/path/to/script2.sh &

**/newly/inserted/path/to/script3.sh &**

exit 0
```

What's the best way to go about doing this?

---

### Post by cortman on 2012-09-28
Use sed:

```
sed -i '18i /newly/inserted/path/to/script3.sh &' /etc/rc.local
```

That example writes it to line 18- you'd need to know which line to write it too, so that's not the best universal solution. You could also use 

```
sed -i "/exit 0/i\/newly/inserted/path/to/script3.sh &" /etc/rc.local
```

to write it to the line just previous to "exit 0", which would be more accurate.

---

### Post by Stonecold1995 on 2012-09-28
Thank you!

EDIT: I tried the second method you gave, but rc.local has "exit 0" repeated twice, so that just ends up making rc.local look like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
**/newly/inserted/path/to/script3.sh &**
# Make sure that the script will "*exit 0*" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**/newly/inserted/path/to/script3.sh &**
*exit 0*
```

---

### Post by Lars Noodén on 2012-09-29
You can have it choose the 'exit 0' that is at the start of the line by anchoring the pattern,

```

sed -i "/^exit 0/i\/newly\/inserted\/path\/to\/script3.sh" /etc/rc.local

```

See also

[http://www.zytrax.com/tech/web/regex.htm](http://www.zytrax.com/tech/web/regex.htm)

---

### Post by cortman on 2012-09-29
As Lars says, you can rewrite the regex so that it inserts your text ONLY after lines that begin with "exit 0".

```
sed -i "/^exit 0$/i\/newly\/inserted\/path\/to\/script3.sh" /etc/rc.local
```

This would now limit it to lines containing only "exit 0" and no trailing characters.

---

### Post by Stonecold1995 on 2012-09-29
> **cortman said:**
> As Lars says, you can rewrite the regex so that it inserts your text ONLY after lines that begin with "exit 0".

```
sed -i "/^exit 0$/i\/newly\/inserted\/path\/to\/script3.sh" /etc/rc.local
```

This would now limit it to lines containing only "exit 0" and no trailing characters.

Thank you!

---

### Post by HiImTye on 2012-09-30
if you want to put it before 'exit 0' then you need to do something like this:
```
sed -i 's|exit 0|/newly/inserted/path/to/script3.sh \&\nexit 0|' /etc/rc.local
```
or something like this:
```
sed -i 's|exit 0|/newly/inserted/path/to/script3.sh \&\n&|' /etc/rc.local
```

---

### Post by btindie on 2012-09-30
If "exit 0" is on the last line, which it normally is after a clean install, you can use the following
```
sed -i -e '$ i\/newly/inserted/path/to/script3.sh &' /etc/rc.local
```
which inserts it before the last line.

---

