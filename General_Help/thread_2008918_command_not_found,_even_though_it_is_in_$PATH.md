---
title: "command not found, even though it is in $PATH"
date: 2012-06-23
forum: General Help
---

### Post by iliveinmyworld on 2012-06-23
Hello everybody (:

I have quite an interesting problem and I don't even know where to start:

```

# echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

# ls /usr/bin | grep skype
skype

# skype
zsh: command not found: skype

```Even though /usr/bin is in $PATH and skype in /usr/bin/ it just simply doesn't find the command. The same happens with bash. Skype was working fine, then I didn't use it for a while and now the command can't be found. Can somebody help me? (:
thx

---

### Post by lechien73 on 2012-06-23
Hi and welcome to the forums,

Please could you post the output of:

```
ls -l /usr/bin/skype
```

If the permissions doesn't show as:

```
-rwxr-xr-x
```

Then please type:

```
sudo chmod 755 /usr/bin/skype
```

This will add executable permissions to the command.

---

### Post by iliveinmyworld on 2012-06-23
thanks for your comment. I forgot to add, that the permissions are set correctly:

```

ll /usr/bin/skype 
21M -rwxr-xr-x 1 root root 21M 2011-06-08 12:26 /usr/bin/skype

```

---

### Post by lechien73 on 2012-06-23
What happens if you try to call it with the full path?

```
/usr/bin/skype
```

---

### Post by iliveinmyworld on 2012-06-23
I get the same result:

```

# /usr/bin/skype
zsh: no such file or directory: /usr/bin/skype

```

---

### Post by sudodus on 2012-06-23
Which version (10.04, 11.04, 11.10 or 12.04) and flavour (Ubuntu, Kubuntu, Lubuntu, Xubuntu ...) are you running? Have you upgraded to a new version?

[s]What happens when you issue the command ```
/usr/bin/skype
```
and what happens when you try to run it from the menu?[/s]

Maybe you need to reinstall Skype.

---

### Post by iliveinmyworld on 2012-06-23
I installed a 64bit Lubuntu 11.10 and didn't change it since then. The weird part is, that skype was working perfectly fine (with the few necessary workarounds) and then just simply stopped.
I would actually prefer not to upgrade the system to a newer version as I am quite happy it is working fine (apart from skype) and there are a few things that stop working after a system upgrade (oder need some time to work again).
I will try to simply reinstall skype.

---

### Post by sudodus on 2012-06-23
> **iliveinmyworld said:**
> ...
I will try to simply reinstall skype.

Maybe it would help you to have a look at ```
man apt-get
```
to select the correct commands to keep or wipe the configuration files.

Good luck :-)

---

### Post by iliveinmyworld on 2012-06-23
That did the trick. I just purged it and completely reinstalled it with the workarounds. THanks
Do you know, how this can happen? I didn't even think about reinstalling as the command wasn't even found. Do you know how to explain that?



edit: hehe, thanks. I am using aptitude (: but same principle

---

### Post by sudodus on 2012-06-23
> **iliveinmyworld said:**
> That did the trick. I just purged it and completely reinstalled it with the workarounds. THanks
Do you know, how this can happen? I didn't even think about reinstalling as the command wasn't even found. Do you know how to explain that?

No I can't explain it, maybe you had some error writing to the disk. But you solved the problem: that is the important thing :KS

Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED.

---

### Post by iliveinmyworld on 2012-06-24
thank you (:

---

### Post by iliveinmyworld on 2012-06-24
Thank you (:

---

