---
title: "I can not remove SSH"
date: 2010-02-23
forum: General Help
---

### Post by DrDoS on 2010-02-23
On my ubunutu server box - I found out that my ssh has been hacked

The file size is way over - and I can not remove it via rm -f /usr/bin/ssh even in root I get permission denied.

Any advice?

---

### Post by tubasoldier on 2010-02-23
To remove SSH it is best to remove the actual package.
```
sudo apt-get remove openssh
```

That would be the best way to go, unless you actually use SSH.

As far as any files that may be on your system. You will need sudo/root access to delete any files in /

---

### Post by DrDoS on 2010-02-23
> **tubasoldier said:**
> To remove SSH it is best to remove the actual package.
```
sudo apt-get remove openssh
```

That would be the best way to go, unless you actually use SSH.

As far as any files that may be on your system. You will need sudo/root access to delete any files in /

No dice on that either.

Problem is that my openssh server was hacked and compromised. 
I can not remove the ssh file at all - permission deined in every way. 

I have try apt-get remove , rm, moving it to dev/null , unlinking it
cant even change permission on it - its like locked out on me.

---

### Post by Darkish Dave on 2010-02-23
Can you sudo?

Firstly, Check you sources list for anything suspicious 

```
gedit /etc/apt/sources.list
```

Then try reinstalling SSH, before removeing it.

```
sudo apt-get install --reinstall openssh
```

---

