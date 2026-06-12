---
title: "Bash script for remote terminal"
date: 2011-04-13
forum: General Help
---

### Post by salmontres on 2011-04-13
Hi everyone,

I'm trying to make a cheap bash script that will log me into a remote terminal. So far, this has been working:

ssh -X [email]remote.terminal@whatever.destination.com[/email]

When I run the script, it prompts me for a password. I'd like to include the password entry into the bash script. How do I do this?

---

### Post by earthpigg on 2011-04-13
i believe you want to bark up the tree of "using key authentication instead of password authentication with ssh". 

debian documentation: [http://www.debian-administration.org/articles/530](http://www.debian-administration.org/articles/530)
more debian docs: [http://www.debian-administration.org/articles/152](http://www.debian-administration.org/articles/152)
ubuntu documentation: [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)
arch documentation: [https://wiki.archlinux.org/index.php/Using_SSH_Keys](https://wiki.archlinux.org/index.php/Using_SSH_Keys)

if you can translate 'pacman' commands into 'sudo apt-get' commands reliably, i generally prefer arch's documentation to all others. ubuntu's documentation is generally pretty weak, in my opinion, so if you can't handle arch's, look at the 2 debian articles.


EDIT: the 2nd debian document looks to be the most directly related to your needs.

> ...Once this has been done you should be able to login remotely, and run commands, without being prompted for a password:

```
skx@lappy:~$ ssh mystery uptime
 09:52:50 up 96 days, 13:45,  0 users,  load average: 0.00, 0.00, 0.00
```

---

### Post by salmontres on 2011-04-13
Thanks Earthpigg. This seemed to do the trick!

---

