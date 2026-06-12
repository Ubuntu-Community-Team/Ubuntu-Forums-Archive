---
title: "Shells not detected?"
date: 2012-06-05
forum: General Help
---

### Post by Godestiny on 2012-06-05
Hello,
Someone can help me? I'm trying to switch from sh shell to dash to install a framework.
Dash is present in my /bin directory but when I type:
chsh -l
The shells list fail to show up. 
Even with:
su -s dash
I get "Cannot execute dash: No such file or directory"...
Also when I install my famework, I get this error message:
The installer has detected that your system uses the dash shell
as /bin/sh.  This shell is not supported by the installer.
You can work around this problem by changing /bin/sh to be a
symbolic link to a supported shell such as bash.
For example, on Ubuntu systems, execute this shell command:
   % sudo dpkg-reconfigure -plow dash
   Install as /bin/sh? No
Please refer to the Getting Started guide for more information,
or contact CodeSourcery Support for assistance.
So I tried to use:
sudo dpkg-reconfigure -plow dash
I seems to work but again when I reexecute my framework bin I still have the same message...
Someone know how to solve this?
Thank you

---

### Post by Godestiny on 2012-06-07
no one? :(

---

### Post by steeldriver on 2012-06-07
your post is kind of confusing... did you actually try what the installer suggested?

```
sudo ln -sf bash /bin/sh
```you can always revert it after with

```
sudo ln -sf dash /bin/sh
```

---

### Post by Godestiny on 2012-06-07
Thank you very much, everything works now :)

---

