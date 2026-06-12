---
title: "Suckit Rootkit detected?"
date: 2010-08-17
forum: General Help
---

### Post by Dalek Draco ON LINUX on 2010-08-17
Hi,

I've just ran a chkrootkit and rkhunter check, and they came up with:
**Chkrootkit**:
/sbin/init                                               [ Warning ]
/sbin/runlevel                                           [ Warning ]
Suckit Rootkit                                           [ Not found ]

**Rkhunter**:
Searching for Suckit rootkit...                             Warning: /sbin/init INFECTED

Any help/advice would be greatly appreciated. I have the normal repositories installed, but I've played around a bit, installed some software from linux magazine discs (linux format, and linux user/programmer). But other than that I can't think of anything security compromising that I do.

---

### Post by balaknair on 2010-08-17
It's likely a false positive.
There's a known bug in chkrootkit
[https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566)

Further reading and instructions to figure out if you're really infected
[http://forums.gentoo.org/viewtopic-t-326062-highlight-suckit.html](http://forums.gentoo.org/viewtopic-t-326062-highlight-suckit.html)

---

### Post by Dalek Draco ON LINUX on 2010-08-19
Thanks. I reinstalled after ossec rootcheck also came up with suckit being detected. 

Now chkrootkit and rkhunter are both clean, but for some reason rootcheck is still saying:
[FAILED]: Trojaned version of file '/bin/login' detected. Signature used: 'bash|elite|SucKIT|xlogin|vejeta|porcao|lets_log|sukasuk' (Generic).

I'm hoping this is just another false positive as upon reinstalling (I booted to livecd, reformatted, then reinstalled) I have only installed updates and trusted programs like pidgin, bleachbit etc.

With regards to the article on the gentoo forums...do you happen to have a noobs guide to doing it? I got lost after it said change /sbin :P.

Thanks in advance.

---

### Post by balaknair on 2010-08-19
From the second link I posted above, you could try these steps to check if you're really infected.
[http://forums.gentoo.org/viewtopic-t-326062-highlight-suckit.html](http://forums.gentoo.org/viewtopic-t-326062-highlight-suckit.html)
[I]- The SucKIT rootkit allows an attacker to hide malicious files by giving them a particular ending. The current attacker is hiding code that ends in xrk or mem. To test for the presence of the rootkit, create a file whose name ends in xrk or mem, then execute an "ls -l". If the files you just created are not shown in the output of ls, it means that the rootkit is hiding them, ie. your system is compromised and needs to be rebuilt.

- Change directories to /sbin and execute an "ls -l init" -- the link count should be 1. Create a hard link to init using ln, and then execute the "ls -l init" again. If the link count is still 1, the SK rootkit is installed.

- Rooted systems send usernames and passwords to other compromised machines using TCP port 55, so if you keep records of network connections, traffic to destination port TCP/55 merits further investigation.[/I]

If your box really is infected and a rootkit is among the 'trusted' packages in the repos, it merits a closer look, and the Ubuntu repo package maintainers ought to be notified.

Edit: Noob's guide
> - Change directories to /sbin and execute an "ls -l init" -- the link count should be 1. Create a hard link to init using ln, and then execute the "ls -l init" again. If the link count is still 1, the SK rootkit is installed.
To do this, in a terminal type in
```
cd /sbin
ls -l init
```
you ought to get an output like
-rwxr-xr-x [COLOR="Red"]1[/COLOR] root root 125704 2010-08-13 04:40 init
The one(I've highlighted it in red here) is the count you want

Now
```
sudo mkdir /sbin/test
sudo ln init /sbin/test/init
ls -l init
```

The output should now look something like
-rwxr-xr-x [COLOR="Red"]2[/COLOR] root root 125704 2010-08-13 04:40 init

If you still get a count of one, that means something in the background is hiding stuff- possibly a rootkit.

---

### Post by Soul-Sing on 2010-08-19
imo its a bug: [https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566](https://bugs.launchpad.net/ubuntu/+source/chkrootkit/+bug/454566)
as mentioned by balaknair

---

### Post by Dalek Draco ON LINUX on 2010-08-19
> **balaknair said:**
> From the second link I posted above, you could try these steps to check if you're really infected.
[http://forums.gentoo.org/viewtopic-t-326062-highlight-suckit.html](http://forums.gentoo.org/viewtopic-t-326062-highlight-suckit.html)
[I]- The SucKIT rootkit allows an attacker to hide malicious files by giving them a particular ending. The current attacker is hiding code that ends in xrk or mem. To test for the presence of the rootkit, create a file whose name ends in xrk or mem, then execute an &quot;ls -l&quot;. If the files you just created are not shown in the output of ls, it means that the rootkit is hiding them, ie. your system is compromised and needs to be rebuilt.

- Change directories to /sbin and execute an &quot;ls -l init&quot; -- the link count should be 1. Create a hard link to init using ln, and then execute the &quot;ls -l init&quot; again. If the link count is still 1, the SK rootkit is installed.

- Rooted systems send usernames and passwords to other compromised machines using TCP port 55, so if you keep records of network connections, traffic to destination port TCP/55 merits further investigation.[/I]

If your box really is infected and a rootkit is among the 'trusted' packages in the repos, it merits a closer look, and the Ubuntu repo package maintainers ought to be notified.

Edit: Noob's guide

To do this, in a terminal type in
```
cd /sbin
ls -l init
```you ought to get an output like
-rwxr-xr-x [COLOR=Red]1[/COLOR] root root 125704 2010-08-13 04:40 init
The one(I've highlighted it in red here) is the count you want

Now
```
sudo mkdir /sbin/test
sudo ln init /sbin/test/init
ls -l init
```The output should now look something like
-rwxr-xr-x [COLOR=Red]2[/COLOR] root root 125704 2010-08-13 04:40 init

If you still get a count of one, that means something in the background is hiding stuff- possibly a rootkit.

 I get a 2 on the second output :D. Thank you :D.  solved.

---

### Post by dcstar on 2010-08-20
> **Dalek Draco ON LINUX said:**
> I get a 2 on the second output :D. Thank you :D.  **solved**.

Then **mark** the thread.

---

### Post by Dalek Draco ON LINUX on 2010-08-21
> **dcstar said:**
> Then **mark** the thread.


Sorry didn't realise I was meant to. I take it you just mean put solved in the title?

---

### Post by Iowan on 2010-08-21
> **Dalek Draco ON LINUX said:**
> Sorry didn't realise I was meant to. I take it you just mean put solved in the title?

There's no obligation, but it helps others with similar problems. **dcstar** has the basics in signature - or there's [this]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") How-To. :)

---

