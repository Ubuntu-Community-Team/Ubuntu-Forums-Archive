---
title: "Processes listening to ports - ipv4 | ipv6 only ?"
date: 2011-07-03
forum: General Help
---

### Post by luceerose on 2011-07-03
Here's my situation. I'm running a native dual-stack (ipv4 & ipv6) dsl connection.
So, I've been adding firewall rules, cleaning up unwanted processes, etc to tighten security.

I'm left with only 3 processes that are listening to ports. mysql, ipp & ssh.
Still not quite sure I need mysql. I run Amarok but without using a database, so I don't actually use sql for anything that I'm aware of.
Anyway, my question is;
Is it possible to make any any of these processes listen to ipv4 only or ipv6 only ???
Is there a distinction there at all?

Example- ssh is currently listening to port 22 on both tcp & tcp6. I do all my ssh connections using 'ssh -6', so, Can I make ssh listen to tcp6 only, or ignore tcp ?

---

### Post by lemming465 on 2011-07-04
In general, yes, you can make server processes only do IPv4 or only IPv6 or both.  For ssh this can be controlled either from the command line (-4, -6 options) or in /etc/ssh/sshd_config with the *AddressFamily* option.  Since contemporary Ubuntu is a little confused about whether it is running sshd as an old-style sysV init job or a new-style upstart job, I'd recommend modifying sshd_config.  You address family options are BSD style, namely "inet" for v4, "inet6" for v6, or "any" for both.  E.g. to only listen to v6 put in:```
AddressFamily inet6
```
SSH is a TCP-based protocol, so you are going to have to commit to at least one of those if you want to use it at all.

The other two are left as an exercise for the reader :-(  The man pages for the server daemon and its config file (e.g. sshd, sshd_config) will usually explain what your options are.

---

### Post by luceerose on 2011-07-05
Thanks heaps.
Adding 'AddressFamily inet6' to sshd_config worked like a charm.

I think I'll leave ipp listening to both stacks for now.
I've got a network printer hooked up to my router on an ipv4 address. I'm not even sure the router will let me connect to the printer using ipv6, so I'll address that further down the track.

If anyone would like to throw in an opinion regarding the mysql, please do.
In any case, I'm marking this one solved. Thanks again, lemming.

---

### Post by luceerose on 2011-07-05
New Information.

I found the following in the sshd_config file;
```
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
```
Just uncomment one or the other.

This way & the AddressFamily method both work.

The ListenAddress method makes more sense to me.
Once ipv4 is history, we'll have no need to specify family (inet or inet6).
So then, we'll just have ListenAddress with the option of listening to a single address or :: or a specified range.

---

