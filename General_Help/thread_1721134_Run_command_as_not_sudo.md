---
title: "Run command as not sudo"
date: 2011-04-04
forum: General Help
---

### Post by cbob on 2011-04-04
Hello,
I have written a script that must be run as root, but at one point in the script there is some library configuration which should not be run as root. 
So my question, is there a command that runs another command as _not_ root when root? (If that makes any sense..)

Regards,
cbob

---

### Post by mendhak on 2011-04-04
What about - just for that specific line - you use

sudo -u cbob YourCommandHere

I believe you can also, from within the script, do this:

su cbob -c 'YourCommandHereInSingleQuotes'

I do not know which is the better way.

---

### Post by SeijiSensei on 2011-04-04
> **mendhak said:**
> I do not know which is the better way.

You must encase the command in quotes if it contains embedded spaces.  If the command requires passed environment variables then use double quotes.  Single quotes tell bash to parse the embedded string literally.

```

TEST=hello
echo "$TEST" 
echo '$TEST'

```

The first command will return "hello", the second will return "$TEST".

---

### Post by mendhak on 2011-04-04
Ah thanks for that, I'm new to Ubuntu as well so my knowledge isn't perfect yet :D

---

### Post by cbob on 2011-04-05
Thanks for your replies,
The script i'm writing is for any system and should not have a static username in it, anyway to do 
```
# su cbob -c 'echo $USER'

```
more dynamic?

---

### Post by deathadder on 2011-04-05
> **cbob said:**
> Thanks for your replies,
The script i'm writing is for any system and should not have a static username in it, anyway to do 
```
# su cbob -c 'echo $USER'

```
more dynamic?
$USER will still be root:
```

# whoami
root
# cat myRootTest.sh
#!/bin/bash

su system -c 'echo $USER'
# ./myRootTest.sh
root
#
```
What you need to do is put a dash before the username.
```

# cat myRootTest.sh
#!/bin/bash

su - system -c 'echo $USER'
# ./myRootTest.sh
system
#

```
The dash creates a login shell so $USER, and other environment variables, get set correctly...

Unless I've misunderstood what you're trying to do :)

---

### Post by cbob on 2011-04-05
Maybe its a fluke but it works both aways for me :P
I'm trying to run a command as not root when root, without knowing any usernames..

---

### Post by SeijiSensei on 2011-04-05
> **cbob said:**
> Maybe its a fluke but it works both aways for me :P
I'm trying to run a command as not root when root, without knowing any usernames..

:confused:

Some user needs to own the process that runs the command.  If it's not going to be root, it needs to be another existing user.  User "nobody" is often a good choice since it should exist on any system. Try

su nobody -c 'command'

---

### Post by cbob on 2011-04-06
Thanks a lot! Thats solved it all:D

---

