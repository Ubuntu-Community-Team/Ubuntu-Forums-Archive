---
title: "sudo apt-get ******* wont work."
date: 2011-02-01
forum: General Help
---

### Post by alannerd on 2011-02-01
I dont know what I may have done wrong, but I just installed ubuntu server.

Whenever I type "sudo apt-get ??????" it wont download whatever it is i typed.

I tried telnetd, openssh-server, etc....nothing worked.

It keeps telling me "unable to find package ??????"

What am I doing/did wrong?

-Alan

---

### Post by alannerd on 2011-02-01
Oh and its actually "sudo apt-get install ???????" 

mistyped.....

---

### Post by fret669 on 2011-02-01
Is it a fresh install?

Not sure I've ever had that issue.

---

### Post by alannerd on 2011-02-01
yep just installed it last night. Everything seemed to install fine...but no love on apt-get

---

### Post by alannerd on 2011-02-01
I do have IP connectivity, my DNS is set up correctly as I can ping google.com & yahoo.com.

So I cant imagine why it cant find it.

---

### Post by bapoumba on 2011-02-01
It would help you post the errors you get, for ex to sudo apt-get update, thanks.

---

### Post by robert shearer on 2011-02-01
"sudo apt-get install ???????" 
you cant search for package > ???????

you need to specify a package name..

that's why it says..
> "unable to find package ??????"

(there is no such package)

what package do you want to install ?.

---

### Post by bodhi.zazen on 2011-02-01
Use apt-cache to search for packages.

```
apt-cache search foo
```

---

### Post by alannerd on 2011-02-01
> **robert shearer said:**
> "sudo apt-get install ???????" 
you cant search for package 

you need to specify a package name..

that's why it says..


(there is no such package)

what package do you want to install ?.

[QUOTE=alannerd]I tried telnetd, openssh-server, etc....nothing worked.[/QUOTE]

I didnt actually search ??????, I did telnetd, openssh-server, etc....

I just put ?????? to indicate that EVERYTHING I had tried it on wasnt working.

---

### Post by lisati on 2011-02-01
Were the asterisks on purpose or did the forum's filtered words list kick in? :D

---

### Post by alannerd on 2011-02-01
> **bapoumba said:**
> sudo apt-get update

That did the trick...apparently it just needed to be updated.

THANKS!

---

### Post by alannerd on 2011-02-01
> **lisati said:**
> Were the asterisks on purpose or did the forum's filtered words list kick in? :D

On purpose. I switched from ****** to ??????, and I have no idea why. ;)

---

