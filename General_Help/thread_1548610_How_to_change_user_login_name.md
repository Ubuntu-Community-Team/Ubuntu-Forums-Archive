---
title: "How to change user login name?"
date: 2010-08-08
forum: General Help
---

### Post by UranUtan on 2010-08-08
Hi,

I created a user with Desktop privileges. Made some cools GUI customizations for a nice desktop. Then for whichever reason, I want to change the user name (the lowercase 1 word name used for login, not the display name).

What is the most efficient way to do this?

Thanks in advance for any help.

---

### Post by chopinhauer on 2010-08-08
Users don't usually change their username, so the procedure is not straightforward. You have to change your username in /etc/passwd (and its counterpart /etc/shadow). For coherence's sake you'd want probably move your home directory to the new name (and update the entry in /etc/passwd) and change your main groupname (which usually is equal to your username) in /etc/group and /etc/gshadow to reflect the change in username.

---

### Post by UranUtan on 2010-08-08
Hi,

This sounds complicate. I didn't elaborate on the reason why I wanted to change the user name. A typo made on a name from a different culture could possibly become offending.

Would it be simpler to create a new user, copy the content of the home folder of the old user to the new one and delete the old user account completely?

---

### Post by chopinhauer on 2010-08-09
> **UranUtan said:**
> 
Would it be simpler to create a new user, copy the content of the home folder of the old user to the new one and delete the old user account completely?


If it is easier for you, that's the right solution. Otherwise change all occurrences of the old username in /etc/passwd /etc/shadow /etc/group /etc/gshadow and rename the home directory.

In a script you can do it as:
```

#!/bin/bash
if [ $# -lt 2 ]; then echo "Usage: $0 olduser newuser"; fi
old="$1"
new="$2"
for i in /etc/{passwd,group,{,g}shadow}; do
  ex $i <<COMMANDS
  %s/\<${old}\>/${new}/g
  wq
COMMANDS
done
mv /home/{$old,$new}

```

---

### Post by UranUtan on 2010-08-09
Wow this is a geeky solution which is definitely faster than the poorman's version I was thinking of.

Merci beaucoup.

---

