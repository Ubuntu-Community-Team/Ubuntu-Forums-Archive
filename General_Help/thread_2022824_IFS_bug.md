---
title: "IFS bug?"
date: 2012-07-11
forum: General Help
---

### Post by LuniTux on 2012-07-11
Hello,

I have a script that seems to have a glitch with IFS.

If I run the script as a normal user, I get:

```
-rw-r--r-- root root /var/www/Shared/contacts.html
-rw-r--r-- root root /var/www/Shared/index.html
-rw-r--r-- root root /var/www/Shared/layout.css
-rw-r--r-- root root /var/www/Shared/settings.js
```

But if I run the script using sudo, I get:

```
-rw-r--r-- root root /var/www/Shared/co
tacts.html
-rw-r--r-- root root /var/www/Shared/i
dex.html
-rw-r--r-- root root /var/www/Shared/layout.css
-rw-r--r-- root root /var/www/Shared/setti
gs.js
```

And here is the script:

```
oIFS="$IFS"
IFS=$'\n'
for line in `cat 'old_permissions'`; do
	echo $line
done
```

It seems that the "n's" in the filenames are becoming linebreaks... Is this a glitch or is my code wrong?

Thanks,

---

### Post by Vaphell on 2012-07-11
add hashbang ```
#!/bin/bash
``` probably root doesn't use bash and the shell used doesn't recognize the $'...' construct, so the separators are $ and n

besides use while to iterate over files and command outputs, it eliminates the need for touching IFS altogether

```
while read -r line; do
  echo $line
done < file

while read -r line; do
  echo $line
done < <( command )
```

---

### Post by LuniTux on 2012-07-12
Yay that fixed it!

---

### Post by asmoore82 on 2012-07-12
Mangling the IFS introduces a whole class of bugs into shell scripts that can and should be easily avoided...

```
[COLOR="Red"]#wrong, even with IFS hacks...
for file in `ls /some/dir`; do ...[/COLOR]

[COLOR="Purple"]#right, bug free, no IFS hacks needed...
for file in /some/dir/*; do ...[/COLOR]
```

In your case:

```
[COLOR="Red"]#naughty IFS hacks...
oIFS="$IFS"
IFS=$'\n'
for line in `cat 'old_permissions'`; do
	echo $line
done[/COLOR]

[COLOR="Purple"]#not necessary ...
cat old_permissions | while read line
do
    echo "$line" #note below
done[/COLOR]
```

Also note the quotation marks. At first glance in the following you may think that read is eating whitespace which is undesirable. But it's actually caused by the lack of quotes with the echo statement.
```
**$ read line**
test   123
**$ echo $line**
test 123
**$ echo "$line"**
test   123
```

---

