---
title: "sudo not respond"
date: 2009-11-10
forum: General Help
---

### Post by tazir on 2009-11-10
Just installed Xubuntu 6.06 in old notebook (Thinkpad 1161).
There have no response for any sudo command I type (include "sudo -h"), other commands work well.
Thanks

---

### Post by sh4d0w808 on 2009-11-10
Try 'man sudo' without quotes.

---

### Post by 3rdalbum on 2009-11-10
When you use 'sudo', it asks you to type your password. Type it. There will not be any stars or symbols put into the terminal when you type. After you've typed your password, hit the Enter key and the command should run.

---

### Post by garvinrick4 on 2009-11-10
Are you trying to be root or use command such as sudo apt-get whatever.
But do the man sudo like suggested and read manual.
root can get you in trouble.  There are a few ways to get to root just different meanings.
For sudo -i or sudo -s or sudo -s -H  and so on and so on. 
If you ever get confused while learning just type "whoami" it will tell you what you are logged in as.   Have fun with Linux.

---

### Post by coffeecat on 2009-11-10
The OP is using Dapper. Perhaps the sudo options that don't work were not implemented back in that dim and distant past.

**tazir**, fwiw, 'sudo -h' in Karmic gives me this output:

> $ sudo -h
usage: sudo [-n] -h | -K | -k | -L | -V | -v
usage: sudo -l[l] [-AnS] [-g groupname|#gid] [-U username] [-u username|#uid]
            [-g groupname|#gid] [command]
usage: sudo [-AbEHnPS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] [-g groupname|#gid] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AnS] [-C fd] [-g groupname|#gid] [-p prompt] [-u
            username|#uid] file ...
... so you're far better off with 'man sudo'. :wink:

By the way, 6.06 came to end of life last July. You might want to install a later version of Xubuntu, so that you can continue to get updates. Why not 8.04? That's an LTS like 6.06 and supported for another 18 months on the desktop.

---

### Post by tazir on 2009-11-10
1. Its Thinkpad 1161, and the best dist is 6.06 ([http://ubuntuforums.org/showpost.php?p=4587507&postcount=4](http://ubuntuforums.org/showpost.php?p=4587507&postcount=4))
2. I was try to run some command, i.e. "sudo apt-get" , but any sudo (**include** "sudo -h", "sudo -i" "sudo apt-get ..." etc. - what I use for test, not to get help) just stuck

---

### Post by coffeecat on 2009-11-10
> **tazir said:**
> 1. Its Thinkpad 1161, and the best dist is 6.06 ([http://ubuntuforums.org/showpost.php?p=4587507&postcount=4](http://ubuntuforums.org/showpost.php?p=4587507&postcount=4))

Have a look at that link again. **It's 18 months old**. It was posted before 8.04 was released. The poster was unable to get 7.10 installed, but there have been 4 releases since. One of them might work.

> **tazir said:**
> 2. I was try to run some command, i.e. "sudo apt-get" , but any sudo (**include** "sudo -h", "sudo -i" "sudo apt-get ..." etc. - what I use for test, not to get help) just stuck

From the wording of your first post it sounded as though some sudo commands were not working, but others were. But now it sounds as though sudo isn't working at all. It might be fixable, but you'll still end up with an unsupported version of Ubuntu.

Have you tried any of the still-supported versions of Ubuntu on that machine: 8.04, 8.10, 9.04, 9.10?

---

### Post by sh4d0w808 on 2009-11-10
Okay, then let's start again from the beginning.

What happens, when U try sudo? Absolutely nothing or error message?

---

### Post by tazir on 2009-11-10
I was trying 9.10 before.
not work, neither the live CD nor the installation.

Just had fresh installation of 6.06, and now sudo work.

---

