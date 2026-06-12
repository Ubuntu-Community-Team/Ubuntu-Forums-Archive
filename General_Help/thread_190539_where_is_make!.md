---
title: "where is make?!"
date: 2006-06-06
forum: General Help
---

### Post by ap.sampson on 2006-06-06
I downloaded the Dapper Kubuntu CD and installed.  I use a PCI ethernet card - and no drivers were installed.  No biggy, I went to 3com on a different box, downloaded it and copied it over.

Now the problems arise, I DON'T HAVE MAKE!  No make.  I type make and it says make doesn't exist. So, i checked /usr/bin and sure enough, no make.

I'm wondering:
1) has anyone else had this problem - is there a reason make isn't installed?
2) how do I go about getting it?

---

### Post by thasheep on 2006-06-06
To get make, and all the other standard compilation tools,
```
sudo apt-get install build-essential
```

---

### Post by givré on 2006-06-06
make and gcc are not installed by default.
Install them simply by 

```
sudo apt-get install built-essential
```

EDIT: faster than me man :cool:

---

### Post by .t. on 2006-06-06
I'm definately going to be supporting the move in Edgy to include build-essentials in the default install, as they are, well, essential!

---

### Post by givré on 2006-06-06
[QUOTE=.t.]I'm definately going to be supporting the move in Edgy to include build-essentials in the default install, as they are, well, essential![/QUOTE]
I support.
Linux without make isn't linux

---

### Post by DoktorSeven on 2006-06-06
In theory I agree that the build-essential stuff should be in there, I think the point of view of Ubuntu is that a standard Linux install for the average person doesn't really need it since most won't be compiling their own stuff anyway, and for those that do, it's only a quick apt-get away.

In other words, I wish it would be included, but I can understand why it's not.

---

### Post by thasheep on 2006-06-06
It's always been one of the first things I've installed when installing (k)ubuntu but if your capable of downloading source and then typing './configure && make && sudo make install', you should be able to manage 'sudo apt-get install build-essential'

---

### Post by shuttleworthwannabe on 2006-06-06
[QUOTE=DoktorSeven]In theory I agree that the build-essential stuff should be in there, I think the point of view of Ubuntu is that a standard Linux install for the average person doesn't really need it since most won't be compiling their own stuff anyway, and for those that do, it's only a quick apt-get away.

In other words, I wish it would be included, but I can understand why it's not.[/QUOTE]
I will beg to differ here: a quick trip to the *-look.org will tell the user that is interested in cutomizing his desktop to learn how to compile. So generally essential I think.

---

### Post by Brachabre on 2006-06-06
I would recommend some way of getting build-essentials put into future ubuntu releases as i'm always looking for "make" myself whenever i do an install :(

---

### Post by graigsmith on 2006-06-06
i usually end up installing it, because, there are certain things like, dosbox, for instance, that i just end up compiling myself, cause the latest versions aren't in the repositories.

---

