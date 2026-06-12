---
title: "slrn problems in ubuntu 10.04"
date: 2010-05-17
forum: General Help
---

### Post by tangential on 2010-05-17
I've installed Ubuntu 10.04 (sweet!) and installed slrn as I am accustomed to using it. 

Unfortunately, I am encountering three problems which I cannot find reference to in the slrn manuals or by searching online. I'm hoping that this is because the nature of the error is simple and obvious to People With Clue.  

The first problem is that though I set the NNTPSERVER to my server name in the command line as required (ie: NNTPSERVER='my.server' && export NNTPSERVER), it does not persist. Once I close slrn and the terminal, then open a new terminal and new instance of slrn, it cannot find the the NNTPSERVER environment variable. 

The second problem is that the .jnewsrc-lock *does* persist, and locks slrn after I close it so that I have to open the .jnewsrc file and delete the PID number and save the empty file so that I can start slrn. 

The third problem (which I've paid less attention to but will mention because it is likely to be related) is that I get a notification when I do start slrn (and sorry, I can't duplicate that error without waiting for some time) that my .newsrc file is out of date and would I like to use another version Y/N?

Any help or suggestions would be greatly appreciated.

---

### Post by tangential on 2010-05-20
Well, I've been poking about and all I can work out is that the slrn process is not shutting down properly until I close the terminal it was running in. 

Of course, then it loses the NNTPSERVER setting and I have to reenter it when I open slrn in a new terminal.

And the third problem refers to the backup being newer than the .jnewsrc file itself. 

All rather perplexing for someone with as little knowledge as me.  I am spending way too much time on this, but I can't seem to help it. :(

---

### Post by andrew.46 on 2010-06-02
Hi tangential,

Good to see another slrn user :). I presume you have seen the quite detailed guide for slrn under Ubuntu here:

slrn - Community Ubuntu Documentation
[https://help.ubuntu.com/community/slrn](https://help.ubuntu.com/community/slrn)

which some kind soul has put together!

> **tangential said:**
> The first problem is that though I set the NNTPSERVER to my server name in the command line as required (ie: NNTPSERVER='my.server' && export NNTPSERVER), it does not persist. Once I close slrn and the terminal, then open a new terminal and new instance of slrn, it cannot find the the NNTPSERVER environment variable.

The easiest solution is to place this information in $HOME/.bashrc and that way it will be available without the need to manually type the information in each time.
 
> The second problem is that the .jnewsrc-lock *does* persist, and locks slrn after I close it so that I have to open the .jnewsrc file and delete the PID number and save the empty file so that I can start slrn. 

As you mention in your next post perhaps you have not been shutting slrn down properly, although with my own copy of slrn the lock file is still deleted even if slrn is not shut down properly...

> The third problem (which I've paid less attention to but will mention because it is likely to be related) is that I get a notification when I do start slrn (and sorry, I can't duplicate that error without waiting for some time) that my .newsrc file is out of date and would I like to use another version Y/N?

Would it be easier to start afresh? Thus delete your $HOME/.jnewsrc file and start again with:

```
slrn -f ~/.jnewsrc --create
```

This might be the easiest way to clear the problem, although you would have to reenter all of your subscribed groups... BTW are you aware that the 'home' for slrn is news.software.readers? You might find that this is the best place to go to with slrn problems.

All the very best,

Andrew

---

