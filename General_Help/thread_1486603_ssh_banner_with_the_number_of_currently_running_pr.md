---
title: "ssh banner with the number of currently running processes"
date: 2010-05-18
forum: General Help
---

### Post by umeboshi80 on 2010-05-18
Hi!

I would like to do the following: Create a banner for any user logging in through ssh which warns him/her about the number of processors being used already by other users (or conversely the number of free processors). For example, if a user logged in he would then see a message like: Warning! 7 out of 8 processors are in use.

I already figured out how to do a banner and with ps -e -o pcpu I can get all processes' %CPU usage. I think I would like to count the number of processes which have more than 90% CPU usage and output this number ("7" in the example) in the banner.

How does one do that?
Thanks,
Hadassa

---

### Post by BoneKracker on 2010-05-18
Since the sshd banner is presented _before_ authentication, it's a bad idea to include information that could be useful to an attacker.  The banner should be more like a warning that unauthorized users who attempt to connect will face prosecution or something.

I think a better idea would be to put a small block of code at the bottom of your users' shell login file (~/.bash_profile, ~/.bash_login, or the equivalent file for the shell you are using).  This is executed _after_ authentication.  The code would simply need to output what you want displayed.  Also, this is much simpler than trying to dynamically alter the contents of a Banner file.

If you want this to apply to all future uses you may add, you can also put it in /etc/skel (for example, in /etc/skel/.bash_profile).  The contents of this directory are copied to newly-created user home directories.  (If you browse /etc/skel, keep in mind that all the files there are dot-files, so you have to "ls -a" or "show hidden files" to see them).

---

### Post by umeboshi80 on 2010-05-18
So I guess I will change motd etc. in order to include this information.
Thanks!

---

### Post by BoneKracker on 2010-05-18
> **umeboshi80 said:**
> So I guess I will change motd etc. in order to include this information.
Thanks!

No, like the banner, motd is not easy to efficiently alter dynamically.  (You could have a running process or a cron job that keeps running 'sed' and putting the current data in there, but that's an awful waste of resources just to have up-to-date data in there for when a user happens to log in.)  Motd is more for static (daily-changing) information.

The other alternative would be /etc/issue (or /etc/issue.net), but like the banner, those are output prior to authentication, and they are similarly difficult to update with data that are not already built-in /etc/issue parameters (see 'man agetty').

Try what I suggested.  It's simple.  If you want to test it, just stick this at the bottom of your ~/.bash_profile file:```
echo -e "\nHey this works. I'm on $(uname -r)\n"
```Just figure out the code to display what you want (about processes or processors or whatever you had in mind).

---

### Post by umeboshi80 on 2010-05-18
Sorry, only saw part of your message when I replied.
Will try your suggestions!
Thanks a lot!

---

### Post by BoneKracker on 2010-05-18
I have a bad habit of editing my messages after posting. :P

---

### Post by rnerwein on 2010-05-18
hi [umeboshi80]("http://ubuntuforums.org/member.php?u=852225")
i think the method you will choose has not much sense. the usage of the cpu must not nessecarily tell you the load
of your system. even with 100 % of cpu usage your system can perform very well. we got schedulers. it's the matter
what is going on on the system ( e.g. heavy IO on the same disk on different partitions .... ).
you can use: uptime to see to how many users logged in and the [COLOR=Blue]load average[/COLOR] !
hope this help
ciao

---

### Post by BoneKracker on 2010-05-18
> **rnerwein said:**
> hi [umeboshi80]("http://ubuntuforums.org/member.php?u=852225")
i think the method you will choose has not much sense. the usage of the cpu must not nessecarily tell you the load
of your system. even with 100 % of cpu usage your system can perform very well. we got schedulers. it's the matter
what is going on on the system ( e.g. heavy IO on the same disk on different partitions .... ).
you can use: uptime to see to how many users logged in and the [COLOR=Blue]load average[/COLOR] !
hope this help
ciao

For that, you can just put this at the end of your ~/.bash_profile```
/usr/bin/uptime
```


The following will give you the 1-minute load average (instead of all three averages included in 'uptime'), the amount of RAM in use, and the amount of Swap in use, and the local date/time on the remote system:

```
read -d' ' ld < /proc/loadavg

echo "    Load: $ld $(awk '
        NR == 3 { printf "  RAM: %u MiB ", $3 }
        NR == 4 { printf "  Swap: %u MiB ", $3 }
        END { print strftime("  %a %b %-e  %T") }' < <( free -m ))"
```

If you wanted, you could display that on login by putting at the bottom of ~/.bash_profile.  Or you could come up with something similar (shorter) and include it in your bash prompt.

Another useful command that pretty much gives you a complete picture of what kind of stress the system under is 'vmstat':
```
~ # vmstat
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 0  0      0 425660 147000 100944    0    0    43     7  216  291 15  2 83  1
```

---

