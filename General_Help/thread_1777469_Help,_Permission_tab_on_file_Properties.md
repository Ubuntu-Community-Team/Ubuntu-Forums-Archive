---
title: "Help, Permission tab on file Properties"
date: 2011-06-07
forum: General Help
---

### Post by ThatCoolGuy220 on 2011-06-07
How can hide it ?

Or unless to request a password?

I want to do this because Sometimes My cousins use my PC and I don't really want to set an account for each one so I let them use the mine.

Problem is I have important files that i don't want to hide but to make them unerasable (I doubt that word exist though)

I mean to not let them erase them but some are pretty clever and they Know of the properties option so they can change the attributes. 

so If i Do something a little more complex (Not much)

They wouldn't be able to erase my stuff:popcorn:

---

### Post by ThatCoolGuy220 on 2011-06-07
Sorry for double posting,

I must add that its not such a big deal since I can access nautilus as root

So I can erase them if I want to..

The problem is the properties option not having a password or not hiding the permissions tab making it very insecure for my stuff

---

### Post by hakermania on 2011-06-07
Well, if I understood, you are the administrator and you have its passwd, so, become root and change the permissions to the important files to root by giving
```
chown root:root files
```
this way the simple user would not be able to delete these files

---

### Post by cracker89 on 2011-06-07
[http://ubuntuforums.org/showthread.php?t=1322037](http://ubuntuforums.org/showthread.php?t=1322037)

---

### Post by ThatCoolGuy220 on 2011-06-07
Thanks now root owns them.

---

### Post by cracker89 on 2011-06-07
---

---

