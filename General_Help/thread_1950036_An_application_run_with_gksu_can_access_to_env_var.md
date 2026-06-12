---
title: "An application run with gksu can access to env variable exported in bashrc of root?"
date: 2012-03-31
forum: General Help
---

### Post by Luca Borrione on 2012-03-31
Hello,

I'm using unison and need to start it from root because the paths I have to sync are writable only from root and I don't want to change their permission, just to avoid the case I forget to change them back.

Ways I can start unison are different depending on the amount of changes:
1. alt+f2 and type ```
gksu unison
``` if I prefer to use the gui which list all the differences in a more comfortable way for me.

2. ctrl+alt+t or ctrl+alt+f1 and type ```
sudo unison profile
``` to run it without gui directly from the terminal, when I don't care too much to check all the differences.

Since I also want to set a unique UNISONLOCALHOSTNAME environment variable, I added 
```
[COLOR="blue"]export UNISONLOCALHOSTNAME=my-pc[/COLOR]
``` to [COLOR="blue"]root's .bashrc[/COLOR] (and to be completely sure also to root's .profile).

Now this is exactly my doubt:
**are all the above methods able to access to UNISONLOCALHOSTNAME set in root's .bashrc?**

For what concerns the terminal shell I saw that if I open a terminal by either hitting ctrl+alt+t or hitting ctrl+alt+f1 and then type
```
sudo printenv | grep UNISON
```
*nothing comes out*, while if I type
```
sudo su
(login as root)
printenv | grep UNISON

```
I get *UNISONLOCALHOSTNAME=my-pc*

So maybe I thought it's better to start unison by typing
```
sudo su
(login as root)
unison profile
```

This can be a solution, even if I would prefer to be able to type directly 'sudo unison profile' just in case I forget.

_Having noticed this behavior (strange for me) I'm afraid that typing directly 'gksu unison profile' can't access to UNISONLOCALHOSTNAME as well like 'sudo printenv' doesn't._

Maybe it's better to use
```
sudo su
(login as root)
gksu unison profile
```

Or even better
```
[COLOR="blue"][B]sudo su
(login as root)
unison-gtk profile[/B][/COLOR]
```

In fact if I run this last one, unison is started as gui and in the shell after my command it prints
```

Connected [//**[COLOR="Blue"]]my-pc[/COLOR]**//mypath -> //**[COLOR="blue"]my-pc[/COLOR]**//mypath-sync]
```
Anyone can clarify that for me, please?
Thank you in advance,

---

### Post by Luca Borrione on 2012-04-01
**I forgot to mention I'm on lubuntu oneiric with unison version 2.32.52**

Anyhow I did some tests:
> 
Added in myUser's .bashrc
export UNISONLOCALHOSTNAME=my-pc-foo-bashrc

Added in myUser's .profile
export UNISONLOCALHOSTNAME=my-pc-foo-profile

Added in root's .bashrc
export UNISONLOCALHOSTNAME=my-pc-bashrc

Added in root's .profile
export UNISONLOCALHOSTNAME=my-pc-profile


Then I opened a terminal and typed
```

foo@my-pc:~$ **printenv | grep UNI**
*UNISONLOCALHOSTNAME=my-pc-foo-bashrc*

foo@my-pc:~$ **sudo printenv | grep UNI**
[sudo] password for foo:
*(no output!!!)*

foo@my-pc:~$ **sudo su**
[sudo] password for foo:
root@my-pc:/home/foo# **printenv | grep UNI**
*UNISONLOCALHOSTNAME=my-pc-bashrc*


```


So:
1. put export in .profile doesn't matter (in fact unison's guide only mentions to add UNISONLOCALHOSTNAME to .bashrc

2. the command 'sudo printenv' cannot access to any exported env variable.

3. It seems I need to first login as root with sudo su to be able to access an env var exported in root's bashrc.


Then I carried on my tests:
**TEST A**
```

sudo su
(login as root)
unison-gtk profile

Connected [//my-pc-bashrc//mypath -> //my-pc-bashrc//mypath-sync]

```
It accesses to root's bashrc exported env and try to store info  under /root/.unison

**TEST B**
```
sudo unison profile
or
sudo unison-gtk profile

Connected [//my-pc-bashrc//mypath -> //my-pc-bashrc//mypath-sync]

```
It accesses to root's bashrc exported env but try to store info  under /home/myuser/.unison

I tried to copy the files unison created under /root/.unison into /home/myuser/.unison but unison doesn't recognize them and try to create new ones.
I tried to rename the first ones with the names unison creates the new ones but unison locks them and refuses to use them.
So unison wants to create different files for different users who fired it.
Finally unison creates a unison.log owned by root:root under /home/myuser/.unison
So this is definitely NOT a recommendable way.

**TEST C**
Using
```

gksu unison-gtk profile
or
gksu unison profile
```
I don't have any string printed like the above 'Connected ..'
so I cannot be sure it accesses to env variables exported in root's bashrc.
Unison tries to create new files under /root/.unison with different names of the test A, but with the same names of the test B
The fact the names are the same suggests me unison can recognizes the env exported and stores this information togheter with the username who fires it.
Renaming the files produced with test A with the names of this new created files produces the same error then in test B (unison locks the archives)
So it seems not possible to start unison from different sudoers and share archives with the last two methods.

**CONCLUSIONS:**
So at the end of my tests I would say:
1. An application can access to an env exported in root's .bashrc for sure when started with:
```
sudo su
(login as root)
applcation

or

sudo application
```

and I think also with ```
gksu application
``` even if I couldn't found how to be 100%  sure of that.

2. In particular if one needs to use unison with root privileges I would recommend to use
```
sudo su
(login as root)
unison-gtk profile
```
and to backup /root/.unison folder, in this way archives can be shared within different sudoers if ever needed.


**LAST NOTE:**
If my first conclusion is right, I cannot understand why 'sudo printenv | grep UNI' prints nothing as I said at the start of this post :(

It would be nice to have your opinion on this too.

---

### Post by HiImTye on 2012-04-01
you can pass environment variables using the sudo command, i.e.
```
sudo env MYVARIABLE=myvariable command
```or you could make an alias in your .bashrc for that command, so that it passes that variable every time you use that command
or you can make a bash script to achieve the same result

---

