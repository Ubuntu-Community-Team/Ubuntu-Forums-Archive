---
title: "Sudoers Help"
date: 2010-09-10
forum: General Help
---

### Post by dardack on 2010-09-10
I'm looking how to allow 1 user the ability to:

sudo apt-get install
sudo apt-get update
sudo apt-get upgrade (this will update packages correct?)

and finally this might not be possible, in a compiled software's directory:
sudo make install

Thanks.

---

### Post by lukeiamyourfather on 2010-09-10
As far as I know users either have sudo or they don't. If someone else has a solution I'm curious to know as well.

---

### Post by philinux on 2010-09-10
> **dardack said:**
> I'm looking how to allow 1 user the ability to:

sudo apt-get install
sudo apt-get update
sudo apt-get upgrade (this will update packages correct?)

and finally this might not be possible, in a compiled software's directory:
sudo make install

Thanks.

But I assume you don't want to give them full admin rights?

---

### Post by dardack on 2010-09-10
> **philinux said:**
> But I assume you don't want to give them full admin rights?

Yes I just want them to be able to update/install but not uninstall stop services etc.

---

### Post by dardack on 2010-09-10
> **lukeiamyourfather said:**
> As far as I know users either have sudo or they don't. If someone else has a solution I'm curious to know as well.

No I know there is a way.  I used to have a bookmark to it.  But I lost everything recently.

---

### Post by philinux on 2010-09-10
> **dardack said:**
> Yes I just want them to be able to update/install but not uninstall stop services etc.

This might help then.

[http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/](http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/)

---

### Post by Bachstelze on 2010-09-10
> **lukeiamyourfather said:**
> As far as I know users either have sudo or they don't. If someone else has a solution I'm curious to know as well.

You are wrong, sudo is much more flexible than that. It is possible to allow users to run only specific commands with sudo, and/or allow them to "impersonate" only specific users (which may or may not be root).

@dardack: Add an entry to your sudoers file like this :

```

john ALL=(ALL) /usr/bin/apt-get, /usr/bin/make

```

User john will be able to run apt-get and make as root with sudo, all other commands will be denied.

---

### Post by dardack on 2010-09-10
> **Bachstelze said:**
> You are wrong, sudo is much more flexible than that. It is possible to allow users to run only specific commands with sudo, and/or allow them to "impersonate" only specific users (which may or may not be root).

@dardack: Add an entry to your sudoers file like this :

```

john ALL=(ALL) /usr/bin/apt-get, /usr/bin/make

```

User john will be able to run apt-get and make as root with sudo, all other commands will be denied.


Don't want all command of apt-get tho, ie apt-get remove/purge I dont' want to allow.

EDIT: is there someway to write a script, ie:

#!/bin/bash
sudo apt-get install %(forget what would go here to get the whole line)

saved as aptgetinstall.sh

john ALL=(ALL) ~/aptgetinstall.sh

---

### Post by Gunman1982 on 2010-09-10
You could create 2 scripts, one to install and one to upgrade, move them to /usr/bin and give the user sudo access to these files. 

Would check if that sudo permission includes changing the scripts tho.

---

### Post by dardack on 2010-09-10
> **Gunman1982 said:**
> You could create 2 scripts, one to install and one to upgrade, move them to /usr/bin and give the user sudo access to these files. 

Would check if that sudo permission includes changing the scripts tho.

Yea don't want that.

Ahh yea dont' put them in home, put them in protected folder and if you dont' give access to an editor should be ok.

---

### Post by dardack on 2010-09-10
So what is the proper way to write the script sudo apt-get install

#!/bin/bash
sudo apt-get install %(what goes here?)

---

