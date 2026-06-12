---
title: "how to download .profile file from the repository?"
date: 2012-03-04
forum: General Help
---

### Post by translatorvasan on 2012-03-04
While following a linux tutorial on editing scripts with vi, it looks I have corrupted the  .profile file in my ubuntu 10.04.
(I have inadverdently deleted the .profile.swp file, too). Even though it does not seem to have affected the functioning of usual commands, I am afraid that problems may come up in advanced usage. To avoid this, I want to download the original .profile file from the repository and replace it with my (doubtfully)corrupted one. Can anybody tell me how and from where I can download it?

---

### Post by wildmanne39 on 2012-03-04
Hi, I do not know how you can do it from the repositories but you should be able to put in the livecd and copy the file from the cd to your installed ubuntu.
Thanks

---

### Post by translatorvasan on 2012-03-04
thank you, wildmanne39.
But I don't have the live cd as of now. 
As another way of solving the problem, 
can you (or anybody else) post your .profile file 
so that I can use it to verify 
whether mine has been corrupted?

---

### Post by raja.genupula on 2012-03-04
may be this 
[http://askubuntu.com/questions/86006/where-is-the-default-bash-profile-file-kept](http://askubuntu.com/questions/86006/where-is-the-default-bash-profile-file-kept)

---

### Post by wojox on 2012-03-04
```
# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

Pretty standard Unity $HOME/.profile :)

---

### Post by wildmanne39 on 2012-03-04
Hi, I see wojox beat me to it and his looks just like mine in 10.04.
Thanks

---

### Post by translatorvasan on 2012-03-04
thank you wojox.
my problem is over.
thanks to wildmanne too

---

### Post by wildmanne39 on 2012-03-04
Hi, your welcome!
Enjoy

---

