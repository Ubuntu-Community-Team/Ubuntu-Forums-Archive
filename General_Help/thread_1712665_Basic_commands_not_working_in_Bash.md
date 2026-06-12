---
title: "Basic commands not working in Bash"
date: 2011-03-23
forum: General Help
---

### Post by diegob51 on 2011-03-23
Hi every body,

I cannot use basic commands in bash such as: ls, dir, echo, grep, etc. None of them is working. No matter what command I try, I always get the same message:

[COLOR="Navy"]bash: /home/diego/bin/dir: cannot execute binary file
[/COLOR]

Any Ideas??

I would really appreciate any help,

Thanks

---

### Post by imblack on 2011-03-23
Can you please tell what exactly happened, or you did, after which they stopped working?

---

### Post by nitstorm on 2011-03-23
bash is looking in ur home folder instead of /usr/bin   ......  Sorry I am not of much help....

Maybe this could be of some help :

[http://www.codecoffee.com/tipsforlinux/articles/030.html](http://www.codecoffee.com/tipsforlinux/articles/030.html)

---

### Post by imblack on 2011-03-23
Since nitstorm gave us a hint, all you need now is to learn how to point bash to look for commands in default directory :)

---

### Post by sj1410 on 2011-03-23
how did you login. 

something wrong with your path. what is the output of the following command.

```

echo $PATH

```

---

### Post by rpaskudniak on 2011-03-23
SJ (Sanjay?) suggested:
> **sj1410 said:**
> how did you login. 

something wrong with your path. what is the output of the following command.

```

echo $PATH

```

Diego may not be able to do this because all of his commands seem to get routed to some subdirectory.  So instead of executing /bin/echo, his bash is trying to run ~diego/bin/echo.  So it is more than just something wrong in his PATH.  Actually, this behavior makes me think that:
[LIST]
[*]The /bin directory has been copied into his $HOME
[*]The copy is imperfect; the binary files do not have the x-flags set. (But then, the PATH-traversal should completely skip them.  So this suspicion is probably wrong.)
[*]And yes, *_his_* bin precedes or has even replaced the true /bin in his PATH.
[/LIST]
Just a suspicion, mind you..

However, Diego, if you type:
```
/bin/echo $PATH
```you override whatever is messed up in your $PATH and should be able to see what the PATH looks like.

How to fix it? you can first stop running bash; go to ksh or sh, using this command:
```
/usr/bin/chsh /usr/bin/ksh
```
Thus, any weird PATH setting you may have in .bashrc or similar file will not be executed and the PATH may be OK, if lacking the stuff you have added.

Then: Rename the $HOME/bin directory to something like $HOME/nobin.  Actually, you ought to rm -rf ~/bin but there might be something under there that really does belong to you.  Also rename your bash startup files so they wont be invoked.  This is temporary, until you can fix them.

Now fix them - edit them to see where PATH is set and get rid of your local ~/bin in there.

OK, this was a mouthful, as usual for me.  (Mr. Concise, yup that's my middle name - Not! :D)

Give it shot - it's very easy to back out your choice of shell.

---

