---
title: "Login Password ok, but password to perform admin tasks not working???"
date: 2010-04-23
forum: General Help
---

### Post by RagsToRich on 2010-04-23
I thought these were the same password?

In-fact, they WERE the same password on the set-up I currently have.

But now, weirdly, I can log in fine but I the exact same password is not using in order to perform admin tasks.

I've tried a recovery mode, console, and then "password (username)" in order to reset the password.

This does reset the password I need to use to log in, but the password still does not work for performing admin tasks.

:confused:

There is only ONE account on my unbuntu system.

---

### Post by sisco311 on 2010-04-23
Hi and welcome to the forums!


Is your user in the admin group?
```
id
```

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by RagsToRich on 2010-04-23
Yes, I checked my sudoers file too.

The error actually comes up as "Incorrect password... try again." even though I'm typing exactly the same password as I used to log in. :confused:

---

### Post by sisco311 on 2010-04-23
> **RagsToRich said:**
> Yes, I checked my sudoers file too.

The error actually comes up as "Incorrect password... try again." even though I'm typing exactly the same password as I used to log in. :confused:

That's a gksu message, does sudo and pkexec in the terminal work?
```
sudo echo
pkexec echo
```

Make sure that the authentication mode in gksu-properties is set to sudo:
```
gksu-properties
```

---

### Post by RagsToRich on 2010-04-23
I found the problem, thanks for the help. As often is the case it was a simple stupid problem...

My login password worked fine right?

But then kicks in that I had my keyboard set to "US international" so I could type spanish charactors easily.

Problem is I have a UK keyboard and my password involves charactors which appear in different places on a USA set-up.

WHOOPS!

Thanks for the help guys :lolflag:

---

