---
title: "Help with aliases"
date: 2006-03-16
forum: General Help
---

### Post by DravenHavok on 2006-03-16
Hello everyone.

I'm trying to create an alias, but it doesn't seem to be working right. Here's what I've been trying: 

```
$ alias [make [=mkdir]] 
```

It doesn't give me an error message after that, but when I try to use "create" to make a directory, it says "command not found". Any help would be greatly appreciated. Thanks a lot!

---

### Post by taurus on 2006-03-16
First of all, there IS a make command in Linux so can't use that alias.  How about this then...
```

alias create=mkdir

```

---

### Post by DravenHavok on 2006-03-16
So I don't need the brakets? Wow thanks so much. I guess I'll go for the create, but thank you for the quick response.

---

### Post by taurus on 2006-03-16
You don't need the brackets and you can't use the brackets, either.  If there is a space between it, then you need to them it in quote as
```

alias rm="rm -i"

```

---

