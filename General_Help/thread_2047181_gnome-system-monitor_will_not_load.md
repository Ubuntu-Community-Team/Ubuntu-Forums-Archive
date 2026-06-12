---
title: "gnome-system-monitor will not load"
date: 2012-08-24
forum: General Help
---

### Post by dmouck on 2012-08-24
Hi everyone,

I have setup several desktops with Ubuntu 12.04 (3.2.0-29-generic x86_64 kernel) that use our LDAP server for authentication and sets their home directory to their user directory in AFS. 

For some reason, this setup will not permit gnome-system-monitor to run. When I attempt to do so, as a regular user, I get the following error :

```
(gnome-system-monitor:3152): ERROR **: Couldn't connect to gnome-system-monitor
Trace/breakpoint trap (core dumped)
```

Checking /var/log/syslog, here is the output:

```
(hostname) kernel: [62470.170511] gnome-system-mo[3152] trap int3 ip:7fcb33ed7fdb sp:7fff129a7df0 error:0
```

I have root enabled on these computers. When I login as root, gnome-system-monitor runs without any problem.

Can anyone assist in parsing these errors or provide information on why this would occur?

Thanks!

---

### Post by Rexilion on 2012-08-24
Maybe you can run a strace with it?

> strace gnome-system-monitor

Maybe it's trying to something funky with the home mount?

---

### Post by dmouck on 2012-08-24
Thanks, Rexilion! I hadn't used the trace command before. The output was nearly 1700 lines long; should I post the output here or direct message it to you?

---

### Post by Rexilion on 2012-08-25
Post it on pastebin.com and post the link here.

Would be nice if you could:

- post a failing strace with the mounted home
- post a non failing strace without the mounted home

Then we could just diff the difference.

---

### Post by dmouck on 2012-08-27
Here are the two pastebins: the first is the output when logged in as a regular user, and the second is with gnome-system-monitor successfully running as root. NOTE: In the first pastebin I renamed the username to USERNAME.

[http://pastebin.com/v3qhW6d8](http://pastebin.com/v3qhW6d8)
[http://pastebin.com/hVhBxXkz](http://pastebin.com/hVhBxXkz)

Happy parsing :)

---

### Post by Rexilion on 2012-08-27
> **dmouck said:**
> Happy parsing :)

Very funny, luckily I know sed a little =). I found the point where they 'split' in behaviour. The output is mangled, beware of that. But does it ring a bell?

> -stat("/Users/managers/USERNAME/.cache/gnome-system-monitor.USERNAME.",)***_=-ENOENT(Nosuchfileordirectory)_***
+stat("/root/.cache/gnome-system-monitor.root.",{st_mode=S_IFSOCK|,st_size=,...})***_= 0 (which is ok!)_***
 socket(PF_FILE,SOCK_STREAM,)=
-bind(,{sa_family=AF_FILE,path="/Users/managers/USERNAME/.cache/gnome-system-monitor.USERNAME."},)=-EPERM(Operationnotpermitted)
-write(,"\n**(gnome-system-monitor:):"...,)=
----SIGINT(Interrupt)@()---
-+++killedbySIGINT+++

---

### Post by dmouck on 2012-08-27
Your sed skills are definitely better than mine :-) . Sed is one thing that I have wanted to spend some time learning.

So I do see the difference, and that when logged in as a regular user, that the file is not being created. I did an -ls -al on the file as root, and saw the following:

srwxr-xr-x  1 root root    0 Aug 27 11:06 gnome-system-monitor.root.3410681331

It looks like that's a socket connection, if I'm understanding my permission bits correctly. I have no clue as to why that file is not created when an LDAP-authenticated user is logged in. It obviously works for regular users and root though. Do you have any ideas or recommendations on where I can look to figure this out? You've been a great help so far, Rexilion, and I appreciate all that you've done.

Cheers

---

### Post by Rexilion on 2012-08-27
> stat("/Users/managers/USERNAME/.cache/gnome-system-monitor.USERNAME.2912353694", 0x7fffa27a2960) = -1 ENOENT (No such file or directory)
socket(PF_FILE, SOCK_STREAM, 0)         = 9
bind(9, {sa_family=AF_FILE, path="/Users/managers/USERNAME/.cache/gnome-system-monitor.USERNAME.2912353694"}, 110) = -1 EPERM (Operation not permitted)
write(2, "\n** (gnome-system-monitor:3817):"..., 84) = 84
--- SIGINT (Interrupt) @ 0 (0) ---
+++ killed by SIGINT +++

It's a permission issue. You should compare the environments of a normal user and an LDAP user. Maybe that might give a clue? GUID? UID? EUID? USERNAME? HOME?

---

### Post by dmouck on 2012-08-27
I ran both env and printenv (which seemed to produce the same output) on both users and didn't see anything that jumped out as being overly different. I'd be happy to pastebin the output of both if you like.

One interesting point that I noticed was in checking the id of both root and the LDAP user. The LDAP users' ID, GID and GROUPS are much higher than a regular (i.e. local) user. Check it out:

root: uid=0(root) gid=0(root) groups=0(root),1094095259

local user: uid=1000(mouck) gid=1000(mouck) groups=1000(mouck),4(adm),24(cdrom),27(sudo),29(audio),30(dip),44(video),46(plugdev),109(lpadmin),119(pulse),120(pulse-access),124(sambashare)

LDAP user: uid=4002(mouck) gid=5000(managers) groups=5000(managers),1094095260

Note that the local user and LDAP users are on different computers. Don't let the same username confuse you. I just wanted to show the difference in the ID and GID numbers. Do you think that could be the issue?

---

### Post by Rexilion on 2012-08-28
> **dmouck said:**
> Note that the local user and LDAP users are on different computers. Don't let the same username confuse you. I just wanted to show the difference in the ID and GID numbers. Do you think that could be the issue?

That definitly raises a red flag! But, does everything else work fine?

---

### Post by dmouck on 2012-08-28
Yep! We have used this setup for awhile in a Fedora environment. I'm trying Ubuntu this year. Everything else appears to be working fine. I'll check with our sr. sysadmin about why the UID and GID are so high in our LDAP server.

---

### Post by Rexilion on 2012-08-29
> **dmouck said:**
> Yep! We have used this setup for awhile in a Fedora environment. I'm trying Ubuntu this year. Everything else appears to be working fine. I'll check with our sr. sysadmin about why the UID and GID are so high in our LDAP server.

Then that is not an issue. It would be best if you could login with the same local user, once authenticated over LDAP and without authentication over LDAP. And check out the differences.

---

### Post by capman on 2012-08-30
I'm having the same problem, but it hasn't been a problem for that long.
Before the vacations this summer it all worked as it should be, must have been after some updates and my customers who reported it don't know exactly when the problem started.

We are using similar systems but also uses kerberos for authentication.

---

### Post by capman on 2012-11-05
Have you found a solution to this yet? I still experince the problem with afshomedir and ldapusers... :/

---

