---
title: "Ubuntu 9.04 - ssh X11Forwarding"
date: 2009-09-24
forum: General Help
---

### Post by oleg_d on 2009-09-24
Hi!
I have a problem with working through Xming, when trying to run X application.
1. Xming, ssh and putty correctly set for run X application in Windows
2. When open ssh session there is message appears 
```
/usr/bin/X11/xauth:  creating new authority file /home/oracle/.Xauthority
```or 
```
/usr/bin/X11/xauth:  /home/oracle/.Xauthority not writable, changes will be ignored
/usr/bin/X11/xauth:  /home/oracle/.Xauthority not writable, changes ignored

```if file already exists
and
: $ xauth list
```
xauth:  error in locking authority file /home/oracle/.Xauthority
```3. Trying to run xeyes for example and get following message
```
PuTTY X11 proxy: wrong authentication protocol attemptedError: Can't open display: localhost:12.0
```4. do ls -la ~/ and there is .Xauthority with root permissions
```
-rw-------  1 root   root        100 2009-09-24 20:07 .Xauthority
```ok, I changed permission  to my owner and xeyes works fine
5. But I need to run oracle installer - runInstaller doesn't work because all files in /tmp directory created with root permissions

So questions - why .Xauthority and files in temp created with root permissions when I trying to do it through ssh+X11forwarding?
I was finding this issue on many site, but didn't find answers

Maybe somebody knows how to resolve this problem

Thanks

P.S. on 8.10 works fine

---

### Post by reesje on 2009-09-24
Hi!
> **oleg_d said:**
> 
```
PuTTY X11 proxy: wrong authentication protocol attemptedError: Can't open display: localhost:12.0
```
I don't know the answer to your question, but I find it odd that it tries to open the localhost display (when logged in on a remote machine localhost refers to that machine (usually 127.0.0.1) AFAIK). I would look for a reason why it tries to do that.
BR,
René

---

### Post by oleg_d on 2009-09-24
it's OK because when I set putty, I put localhost in preferences

---

### Post by oleg_d on 2009-09-24
I found that in ssh session all action made from root.
For example 
```
touch test_file
```
create file in users home with root permissions

Why?

---

### Post by oleg_d on 2009-09-25
Problem SOLVED.
There were permissions for all files in /bin set as 
**```
rwsr-s--x
```**
, so all commands owned by root set permissions as root

Thanks

---

