---
title: "Problem with sudo"
date: 2006-06-06
forum: General Help
---

### Post by yalla on 2006-06-06
Hello,

I have a Ubuntu 6.06 (LAMP) install..

Apache, Mysql and PHP runs fine.. 

My problem is that Sudo does not work. If i put sudo in front to get privilegies, nothing happens..
Example:
$ sudo vi index.php <- noting happens
$ vi index.php <- file opens in vi, but without write privilegies

Same thing with $ sudo apt-get update/upgrade - it asks for my password, then nothing..

Se attached image for example of sudo-problem..

Any ideas?

---

### Post by tonyr on 2006-06-06
What you are describing is what happens if you do not have permission to
run **sudo**.  In a terminal do

```

grep admin /etc/group

```

On my system it shows
```

lpadmin:x:106:tonyr
admin:x:112:tonyr

```

If yours does not look similar (your login instead of mine, of course), that is the problem.

---

### Post by yalla on 2006-06-06
On my system it shows:
```

lpadmin:x:108:
admin:x:110:

```

My username is yalla on the server.. I assume yours is tonyr? And that my output is not what it should be?

How can I fix this?

---

### Post by ifokkema on 2006-06-06
[QUOTE=yalla]On my system it shows:
```

lpadmin:x:108:
admin:x:110:

```

My username is yalla on the server.. I assume yours is tonyr? And that my output is not what it should be?

How can I fix this?[/QUOTE]

If you have access with the root account, you should run:
```
adduser yalla admin
```

Then log in using your account. Run:
```
groups
```
To check if you're in the admin group. Then you should be ready to go.

Ivo

---

### Post by yalla on 2006-06-06
I could not log in using root..

But I managed to add my user to the admin group inside the Webmin interface.

Thank you guys for putting me in the right direction :)

---

