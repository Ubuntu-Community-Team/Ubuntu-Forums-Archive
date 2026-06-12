---
title: "remote dump problem in ext3 dump utility..."
date: 2010-04-02
forum: General Help
---

### Post by charlie1kimo on 2010-04-02
Greetings all,
I don't know if here's a right place to post my question, since it's a bit specific...
okay, so here's the story:
We have two servers running linux, one is Ubuntu and other one is Centos, and recently we are trying to do a system backup.
Since Centos has more hard disk space, we are trying to dump something in ubuntu to centos, then we will image whoe centos system aferward.

So we come to linux etx3 dump utility because our ubuntu disk has ext3 filesystem.

the command I am executing is like the following:
ubunutu> /sbin/dump -f [centos]:[target_path] [to_dumped path]

I did this simply because we are only dumping a small directories in ubuntu, so I don't have to specify level (it's automatically a level 0 dump)

then I got a "useless" error message...
DUMP: [centos] Connection refused.
DUMP: login to [centos] as root failed.
THAT's IT...

so I checked my ssh setup, since I looked up in our ubuntu server, we are using rsh as ssh (it's safer this way I believed.)

I've checked the setup of ssh keys on both server is okay, since I am able to do a simple command like this:
ubuntu> ssh [centos] ls /root

I've also checked the firewall, nothing is blocking port 22 on [centos], otherwise I shouldn't get any output from [ssh] command...

I've also checked the log on [centos]/[ubuntu], but there's nothing log about this...(there's no new logs after I executed the dump command.)

It's a very weird situation...and I am out of idea why this would happened...Does any one familiar with linux ext3 dump utility can answer?

(PS. I didn't setup rsh server on [centos], and rsh != ssh on our [centos] server. But I thought that's okay because we are actually using 'ssh' on [ubuntu])

It's a long thread...Thanks for reading and helping!

-Charlie-

---

### Post by cjhabs on 2010-04-02
I am pretty sure that dump uses rsh, not ssh.
There is a way to get this to work (I had a similar issue under Solaris 10 where rsh was disabled for security), but I don't have access to my notes until Monday.

If you don't get this resolved, drop me a pm to remind me and I'll check how I got it working on Monday.

---

### Post by charlie1kimo on 2010-04-02
so does it mean my server has to setup rsh utility...?
that is sort of painful because I don't want to setup rsh server on our public server...especially I am running my dump as root.

I though ssh/rsh are very similar, I remembered reading some articles about setting rsh as ssh as well...Maybe in theory they would work the same, but I still have to do some tuning in dump <-> rsh <-> ssh...

Thanks for the fast reply!
I doubt I can get this solved before Monday LOL

-Charlie-

---

### Post by cjhabs on 2010-04-03
rsh and ssh are similar only in as much as they both allow remote command execution. rsh is inherently insecure - ssh is way to go.

One solution is to mount the destination folder over nfs and do the dump to the mounted folder - which is now effectively a local operation and does not invoke rsh.

---

### Post by charlie1kimo on 2010-04-09
> **cjhabs said:**
> rsh and ssh are similar only in as much as they both allow remote command execution. rsh is inherently insecure - ssh is way to go.

One solution is to mount the destination folder over nfs and do the dump to the mounted folder - which is now effectively a local operation and does not invoke rsh.

Thanks for the idea!
We actually is doing remote dump to a remote hard drive, so I can just mount the remote hard drive to the machine.
I should have thought of that...LOL

Thanks again!

-Charlie-

---

