---
title: "ssh issue when I use the GUI (works with command line)"
date: 2010-01-26
forum: General Help
---

### Post by a cup of tea on 2010-01-26
This previously worked fine, and I don't know what happened. I am still able to use ssh to connect to my other computer via the command line. If I use Places > Connect to Server, I get an error, either "Error reading from unix: Input/output error" or "ssh program unexpectedly exited".

---

### Post by dallasmayor on 2010-03-10
[B]Do you get the following when running nautilus?
[/B]

**Error: ssh program unexpectedly exited**


ssh works fine in a terminal, but when running nautilus you get the above message. This is cause by an bad locale setting in /home/%user/.config/user-dirs.locale.

Open this file, and it should contain the value "en_US" or what is appropriate for your locale. If it contains the value "C", then it isn't going to work.

---

### Post by Zenguy on 2010-09-05
This looks like a recent SSH bug.

The Arch guys are having the same problem and are attributing it to Nautilus.  [https://bbs.archlinux.org/viewtopic.php?pid=821578](https://bbs.archlinux.org/viewtopic.php?pid=821578)

Their solution is to drop back to an earlier version of SSH.

For the record, I am experiencing this problem too, but not on all my SSH connections. My SSH connection to my Ubuntu server is working great from Nautilus, but when I attempt to connect to my NSLU2 running OpenSlug, then it fails. Command line SSH connection to the NSLU2 works, but the GUI SSH connection is broken. 

I suspect that this must be some kind of incompatibility between different versions of SSH. It's just really strange that the command line version works, since I would have expected it to use the same SSH code as the GUI version.

This is somewhat frustrating, because I was going to use the NSLU2 as a backup server and wanted to use a desktop GUI client backup utility.

---

### Post by leifharmsen on 2010-10-31
I have the same problem.  I can ssh to my Ubuntu 8.04 LTS fine in terminal or using Filezilla or whatever, but when I try with Nautilus' GUI "Connect to Server" it fails with:

Could not open location 'sftp://user@server/var/www'
ssh program unexpectedly exited

(user@server is of course me at my server, removed here)

But I can use nautilus' GUI to connect to another server (a Linux indigo 2.6.26-2-686) with password it works fine.  So there seems to be some incompatibility between the ssh on my 8.04 LTS server and the one in my home desktop (and laptop), but only for Nautilus.  Or maybe there's something wrong with my server, although this seemed to stop working out of the blue, it was working fine before.  Both my desktop and laptop are running 10.04 LTS and I login using a public and private key, no password.

When I follow the [https://bbs.archlinux.org/viewtopic.php?pid=821578](https://bbs.archlinux.org/viewtopic.php?pid=821578) link, the reported error message is different from mine.  When from there I follow the [https://bugs.archlinux.org/task/20724](https://bugs.archlinux.org/task/20724) link, the reported error message is different yet again - plus they say their problem is fixed while mine is not, so mine looks like it may be a different problem.

Home Desktop running 10.04 LTS, update manager says it is up to date.
leif@leif-desktop:~$ ssh -V
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
leif@leif-desktop:~$ nautilus --version
GNOME nautilus 2.30.1
GVFS version is 1.6.1

Server running 8.04 LTS, updated too
user@server:~$ ssh -V
OpenSSH_4.7p1 Debian-8ubuntu1.2, SSH protocols 1.5/2.0, OpenSSL 0x0090807f

> Comment by Otto Allmendinger (OttoA) - Monday, 27 September 2010, 14:39 GMT-4
Fixed upstream in gvfs version 1.6.4
Comment by Ionut Biru (wonder) - Monday, 27 September 2010, 14:44 GMT-4
i pushed gvfs 1.6.4 in gnome-unstable repo

I'd like to try the new gvfs 1.6.4-x but have no idea how to get and install it, which is admittedly noobish of me, and I can not seem to find out how to do such a thing by googling around.  Where is gnome-unstable repo and how do I use it?  I'm really just a frustrated user willing to learn and wanting to fix this.

---

### Post by misanthropist on 2011-01-02
I've got this problem too.
Here is the bug report if anybody else has this problem.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/680295]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/680295")

---

