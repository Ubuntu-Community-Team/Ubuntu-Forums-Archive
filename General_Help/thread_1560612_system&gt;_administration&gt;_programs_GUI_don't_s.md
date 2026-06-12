---
title: "system&gt; administration&gt; programs GUI don't start"
date: 2010-08-25
forum: General Help
---

### Post by mpaesold on 2010-08-25
Hi, 

I'm running Ubuntu 10.4 netbook remix on an Asus Eee PC 1001PX.

uname -a says:
Linux localhost 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

I can't open the GUI for most of the applications in system > administration and some in system > prefernces. In preferences IBus preferences, Main Menu, Prodcast Preferences, Ubuntu One are affected and in administration only Disk Utility, Login Screen, Synaptic, Network Tools, Time & Date, Users & Groups, Update Manager do start (Sorry, that I state the apps that run, but this list seemed shorter to me.). There's just a notification prompted that the program is started but then nothing happens.

Further, the update manager posts a notification in the panel that "A problem occurred when checking for updates." I have the feeling that this occurred at the same time as I couldn't start the programs anymore. Up to now I wasn't able to find out what the problem is, but I didn't touch the software sources.

I read threads about similar problems and there something seemed to be mixed up with the files /etc/hosts and /etc/hostname. But I checked on that and it's fine in my case.

Any help, please?

---

### Post by varunendra on 2010-08-25
AFAIK, /etc/hosts and /etc/hostname are concerned with 'domain-name resolution' only. So they should have nothing to do with your 'prog. not opening' problem.

Have you tried to boot into Recovery Mode & trying dpkg?
(press 'shift' while booting to bring up advanced Grub menu>Select Recovery Mode>Select dpkg.)

Also, I think it'd be interesting to see your host files since the output of uname -a usually contains domain name of the computer, not 'localhost'.

To post the contents, you may use command:
```
cat /etc/hosts
cat /etc/hostname
```

---

### Post by mpaesold on 2010-08-25
Hi, 

I booted in recovery mode and ran dpkg, but it failed to fetch some index files. 

Those are my /etc/hosts and /etc/hostname files

```

martin@mp3:~$ cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    mp3

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
martin@mp3:~$ cat /etc/hostname 
mp3

```

---

### Post by varunendra on 2010-08-25
So the name of your computer is 'mp3'. I'm wondering why it is not displayed in the output of uname -a. Are you using ipv6? Make sure it is set as 'Ignore' under Network Manager.

If you can connect to internet (& thus to the repositories) then maybe your problem can be solved easily. If you are able to open terminal, try & see if you can ping external sites like gmail.com....

---

### Post by mpaesold on 2010-08-26
Hi Varun, 

I disabled IPv6 and browsing is faster now. Awesome! I included the line 'alias net-pf-10 off' in the file /etc/modprobe.d/aliases. I actually had to create that file. Is that normal?

I can surf the net (wired and wireless) and ping is successful.

BTW, the output of uname -a is now

```

Linux mp3 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

```

---

### Post by varunendra on 2010-08-26
> **mpaesold said:**
> I included the line 'alias net-pf-10 off' in the file /etc/modprobe.d/aliases. I actually had to create that file. Is that normal?

Hmm.. so far so good! Since I have never had to create this kind of any file (to be honest- I've no idea about it) & still I always get faster (than windows) browsing on any installation of any linux distro, so I don't think it is normal. (however, I've seen cases on the forum when IPv6 gets enabled automatically & one has to disable it manually.)

Anyway, what about your original problem? Any progress? Are you able to see details of the problem while updating?

---

### Post by mpaesold on 2010-08-26
I checked the documentation, which says that IPv6 is enabled by default and there it also says one should include this line in that file. 

Well, but there's no progress with the original prob so far. Still the admin programs don't start and I have this notification in the panel saying that problems occurred while checking for updates. But if I run the Update Manger it doesn't prompt any errors and just installs the updates.

---

### Post by varunendra on 2010-08-26
Have you got admin rights? Under **User & Groups>(your username)>Advance settings>User Privileges** tab, check if you are being denied any critical right.

I've got 6 unchecked boxes there (all the rest are checked):

[LIST=1]
[*]mount FUSE
[*]send/rec. fax
[*]use audio dev
[*]use floppy drv
[*]use tape drv
[*]use video dev.
[/LIST]
Alternatively, you may try to create a new user (with Administrative rights) and see if the apps open there. If it is not a case of broken install, it should work I guess..

---

### Post by mpaesold on 2010-08-26
Ok, I changed my account settings: no luck.

I created an account with admin rights: no luck.

The thing is that some progs start and some don't. In the very first post of this thread I state the progs that start. The rest just prompts the loading screen and after that nothing happens.

---

### Post by varunendra on 2010-08-26
Yeah, I'm looking back to your first post everytime before posting. It all sounds like a broken system. Especially when you said 'dpkg' failed! Just trying other possibilities I can think of.

What's status of Update settings?

[LIST]
[*]Are all kind of updates ticked?
[*]Are all the repositories in 'Software-Sources' enabled?
[/LIST]
As another shot, try clearing apt-cache files-
```
sudo rm /var/cache/apt/*.bin
```

---

### Post by mpaesold on 2010-08-29
Hi Varun, 

I found out what caused trouble with my system. I installed the enthought python distr on my computer. Then I replaced /usr/bin/python by a symbolic link to the python that came with enthought. Now python doesn't seems to be python. Removing the symbolic link solved the problem.

---

### Post by varunendra on 2010-08-29
Ah.... at last.. !! =D>

Glad you got it solved and really thankful that you cared to share the solution to this 'unique looking problem'.

By the way, how did you find this fix? I couldn't have thought of it myself !!:-k

---

