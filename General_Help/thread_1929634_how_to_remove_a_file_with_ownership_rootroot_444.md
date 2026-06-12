---
title: "how to remove a file with ownership root:root 444?"
date: 2012-02-22
forum: General Help
---

### Post by Luca Borrione on 2012-02-22
Hello!

I created a bootable usb stick of lubuntu using unetbootin.
After using it I wanted to remove everything but I cannot remove a file
```
-r--r--r-- 1 root root 32256 2012-02-21 23:09 ldlinux.sys

```

I tried with
```
$ sudo rm ldlinux.sys
rm: cannot remove 'ldlinux.sys': Operation not permitted 
```
```
$ sudo chmod 755 ldlinux.sys 
chmod: changing permissions of 'ldlinux.sys': Operation not permitted
```
```
$ sudo chown root:users ldlinux.sys 
chown: changing ownership of 'ldlinux.sys': Operation not permitted 
```

Is there any way to get rid of this file other than re-formatting the usb drive?

Thanks

---

### Post by roelforg on 2012-02-22
Bad idea, that file is important, without it linux can't load most of it's programs.

---

### Post by Luca Borrione on 2012-02-22
No no .. the point is that I already used the usb flash for my purpose! I installed lubuntu and I want to free my flash drive again .. doing that I faced the problem described and I found myself unable to remove a file with such ownership in any way. I simply would like to learn how to do it. :)
It seems to me there's no way to remove such a file and the only way is to re-format my pendrive. Am I wrong?

---

### Post by roelforg on 2012-02-22
Run:
```

sudo chown root ldlinux.sys
sudo chmod 777 ldlinux.sys
sudo rm ldlinux.sys

```

---

### Post by Luca Borrione on 2012-02-22
Have you really read my question?

```

$ sudo chown root ldlinux.sys 
chown: changing ownership of 'ldlinux.sys': Operation not permitted

$ sudo chmod 777 ldlinux.sys 
chmod: changing permissions of 'ldlinux.sys': Operation not permitted

$ sudo rm ldlinux.sys
rm: cannot remove 'ldlinux.sys': Operation not permitted

```

As I already wrote in my question ..

---

### Post by roelforg on 2012-02-22
> **Luca Borrione said:**
> Have you really read my question?
Yes, i did.
I noticed that you tried chowning a file whilst not having the user rights to do so;
just copy/paste/exec and it should work.

The point is that if user a owns a file and has higher privs. than user b.
User a has to run chown b <file> to grant user b access.
You tried a file owned be root, with a non-root account.
Hence i added the sudo's.

Which you didn't copy...

---

### Post by Luca Borrione on 2012-02-22
You right: I forgot to include sudo before chown and chmod in my original question. My fault.
Now I will correct them by editing, thank you.

What surprised me is exactly that: I cannot use sudo to solve this issue :(

---

### Post by TeoBigusGeekus on 2012-02-22
Give this command
```
sudo chattr -i ldlinux.sys
```
and then try deleting it again.

---

### Post by Luca Borrione on 2012-02-22
It worked! Thank you so much! I never met the need to use this command before: I'll look at it deeply.
Thank you for helping/teaching me. :)

---

### Post by TeoBigusGeekus on 2012-02-22
Glad to help.

---

