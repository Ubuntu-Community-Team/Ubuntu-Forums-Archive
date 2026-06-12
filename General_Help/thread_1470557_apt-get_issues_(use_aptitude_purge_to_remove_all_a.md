---
title: "apt-get issues (use aptitude purge to remove all associated files of a package)"
date: 2010-05-02
forum: General Help
---

### Post by jbowen7 on 2010-05-02
Did a fresh install of 10.04 Desktop 86_64 this weekend. One of the first issues I noticed right away was that apt was not function properly.

Say for example you install the packages tor and vidalia (assume I'm running everything from root).  
#apt-get install tor vidalia
This command will check and install necessary dependencies, for example 'privoxy'.
Now if you decide that you don't want to use privoxy and instead use polipo, you would probably feel inclined to remove privoxy. Well I found that apt-get autoremove, apt-get remove, apt-get purge WILL NOT remove all the files/directories associated with the package.
You'll find that after running each of these commands, there will still be directories, scripts, etc. in /etc/init, /etc, and /etc/rc*.d.

The only solution I've found to completely removing a package is aptitude purge [package].

---

### Post by dcstar on 2010-05-03
> **jbowen7 said:**
> Did a fresh install of 10.04 Desktop 86_64 this weekend. One of the first issues I noticed right away was that apt was not function properly.

Say for example you install the packages tor and vidalia (assume I'm running everything from root).  
#apt-get install tor vidalia
This command will check and install necessary dependencies, for example 'privoxy'.
Now if you decide that you don't want to use privoxy and instead use polipo, you would probably feel inclined to remove privoxy. Well I found that apt-get autoremove, apt-get remove, apt-get purge WILL NOT remove all the files/directories associated with the package.
You'll find that after running each of these commands, there will still be directories, scripts, etc. in /etc/init, /etc, and /etc/rc*.d.

The only solution I've found to completely removing a package is aptitude purge [package].

So you want apt to somehow figure out that you aren't using a specific package dependency and magically remove all of the associated files?

---

