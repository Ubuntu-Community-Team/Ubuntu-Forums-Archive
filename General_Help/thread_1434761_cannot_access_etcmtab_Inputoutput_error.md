---
title: "cannot access /etc/mtab: Input/output error"
date: 2010-03-20
forum: General Help
---

### Post by 11nux on 2010-03-20
I started a thread about an issue im having connecting to any networks here:
[http://ubuntuforums.org/showthread.php?p=9000324&posted=1#post9000324](http://ubuntuforums.org/showthread.php?p=9000324&posted=1#post9000324)

and i was told by chili555 to start a new thread in this section about an error i'm getting:

```

ubuntu@ubuntu:~$ ls -al /etc | grep resol
ls: cannot access /etc/mtab: Input/output error
ls: cannot access /etc/resolv.conf: Input/output error
drwxr-xr-x   3 root    root        36 2009-10-28 20:58 resolvconf-????????? ? ? ? resolv.conf
-rw-r--r--     1 root    root        23 2010-03-20 03:00 resolv.conf.dhclient-new
-rw-r--r--     1 root    root        53 2010-03-20 14:08 resolv.conf.tmp
-rw-r--r--     1 root    root        30 2010-03-20 02:21 resolv.conf.tmp~

```
This was the last post by chili555:
>   ```
ls: cannot access /etc/mtab: Input/output error
```I don't like the look of this *at all*! It is outside my area of experience and I'd hate to ask you to try fixes that I know little about. I suggest you open a thread on General Help  
So does anyone know how to fix the error  

ls: cannot access /etc/mtab: Input/output error

and whats causing it?


Thanks in advance

---

### Post by chili555 on 2010-03-20
Can anyone (bump!) help us? Thanks.

---

### Post by 11nux on 2010-03-20
> **chili555 said:**
> Can anyone (bump!) help us? Thanks.

Thanks a lot for your help! I hope i can get this going again, don't really wanna reinstall.

---

### Post by garvinrick4 on 2010-03-20
Code: cat /etc/resolv.conf

Post it.

Code: cat /etc/mtab

Post it.

I just noticed ubuntu@ubuntu  this is an edit you need to explain what you want to do.
Ignore this post. I think you need Live CD help. No idea what you want to do.

---

### Post by 11nux on 2010-03-21
ill post those 2 results in the morning when i get on that machine...

I'm booting from a live usb drive but persistently saving changes... I'm just using this for now until i get a new machine to do a full install on. internet always did work on this exact setup for 6 months so it has nothing to do with the live usb boot. Also my Kubuntu live usb currently works 100% with the internet.

I can save everything on my drive, it's an 8gb drive and its set up to let me save all changes.

---

### Post by rnerwein on 2010-03-21
hi
i agree with [garvinrick4]("http://ubuntuforums.org/member.php?u=899097"). looks like a damaged directory entry. you have to use a live CD and run 
fsck manuly. i guess the "cat" won't help you - you will get the same result as you got with ls -la.
wish you luck
ciao

---

### Post by 11nux on 2010-03-21
yeah i got the exact same input/output error when i use cat.

---

