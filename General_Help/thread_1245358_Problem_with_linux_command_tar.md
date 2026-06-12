---
title: "Problem with linux command: tar"
date: 2009-08-20
forum: General Help
---

### Post by masoud23 on 2009-08-20
Hello

when I write this:

tar xvfz xampp-linux-1.7.2.tar.gz -c /opt

i get this message:
tar: You can only give one of flags "-Acdtrux"

what should i do?

---

### Post by bear24rw on 2009-08-20
try
```
tar xvf xampp-linux-1.7.2.tar.gz
```

---

### Post by bostonaholic on 2009-08-20
> **masoud23 said:**
> Hello

when I write this:

tar xvfz xampp-linux-1.7.2.tar.gz -c /opt

i get this message:
tar: You can only give one of flags "-Acdtrux"

what should i do?

I'm guessing you are trying to tar the archive into your /opt directory?

try this

```
sudo tar **xzvf** xampp-linux-1.7.2.tar.gz -**C** /opt
```

You'll need sudo access to write to /opt most likely.  I always use xzvf and I'm not sure if the order matters.  Also  your -c option was to "create a new archive" and I'm guessing you wanted -C "change to directory"

---

### Post by masoud23 on 2009-08-20
> **bostonaholic said:**
> I'm guessing you are trying to tar the archive into your /opt directory?

try this

```
sudo tar **xzvf** xampp-linux-1.7.2.tar.gz -**C** /opt
```

You'll need sudo access to write to /opt most likely.  I always use xzvf and I'm not sure if the order matters.  Also  your -c option was to "create a new archive" and I'm guessing you wanted -C "change to directory"

when i use the comman above i only get: opt/ at next line and nothing happens!

---

### Post by bostonaholic on 2009-08-20
> **masoud23 said:**
> when i use the comman above i only get: opt/ at next line and nothing happens!

It works fine for me.  Are you in the directory where your archive is located?

---

### Post by masoud23 on 2009-08-20
> **bostonaholic said:**
> It works fine for me.  Are you in the directory where your archive is located?

i am in:
```

root@masoud-desktop:~#

```
and archive is there i think:
```

root@masoud-desktop:~# dir
Desktop  opt  xampp-linux-1.7.2.tar.gz

```
and when i write:
```

sudo tar xzvf xampp-linux-1.7.2.tar.gz -C /opt

```
i get
```

opt/

```

---

### Post by bostonaholic on 2009-08-20
I hate to ask but do you have tar installed?  You would get a different error if you didn't.

```
sudo apt-get install tar
```

and why are you logged in as root? in the directory where your archive is located, give us the output of

```
ls -l
```

---

### Post by masoud23 on 2009-08-20
> **bostonaholic said:**
> I hate to ask but do you have tar installed?  You would get a different error if you didn't.

```
sudo apt-get install tar
```

and why are you logged in as root? in the directory where your archive is located, give us the output of

```
ls -l
```

No!! i had not tar installed. i am a newbe! now it is there. I don't know where i should be!!
```

root@masoud-desktop:~# ls -l
totalt 12
drwxr-xr-x 2 root root 4096 2009-08-20 12:01 Desktop
drwxr-xr-x 2 root root 4096 2009-04-20 15:59 opt
-rw-r--r-- 1 root root  106 2009-08-20 19:03 xampp-linux-1.7.2.tar.gz

```
i still can't install with this command: sudo tar xzvf xampp-linux-1.7.2.tar.gz -C /opt

---

### Post by bostonaholic on 2009-08-20
can we see the output of command

```
pwd
```

---

### Post by masoud23 on 2009-08-20
> **bostonaholic said:**
> can we see the output of command

```
pwd
```

root@masoud-desktop:~# pwd
/root

---

### Post by bostonaholic on 2009-08-20
I know you said you're a noob but why are you logged in as root and why are you in the /root directory?  Or is your login username 'root'?

It's odd that you cannot run the command I have given you.  It works perfectly fine for me.  I created a tar.gz and was able to extract it in the /opt directory perfectly fine.

Just to clarify what you're trying to accomplish:

1.  You're in the /root directory
2.  In /root you have an archive named 'xampp-linux-1.7.2.tar.gz'
3.  You're trying to extract said archive into /opt

---

