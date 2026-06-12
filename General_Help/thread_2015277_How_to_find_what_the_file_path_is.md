---
title: "How to find what the file path is"
date: 2012-07-03
forum: General Help
---

### Post by Catlike on 2012-07-03
Sorry it's so basic; I use the terminal rarely, and so have forgotten how to find out the proper file path name for an executable file I'm trying to use. How do I do that?

In general, is there a cookbook-style, how-to-do basic things in Ubuntu somewhere? I keep forgetting the simple things because I don't use them much. 

Thank you.

---

### Post by spikoley on 2012-07-03
I think you are looking for the *which* command.  Below is a command to find *ls*.

```
which ls
```

---

### Post by arubislander on 2012-07-03
Which only works if the the command is in the %PATH% to begin with (can't decide if the pun was intended or not). Most of the time you'd want to no the file path for a command that's not in the environment path...

---

### Post by efflandt on 2012-07-03
To find a command in your $PATH:
**which** route
/sbin/route

I guess finds a command in $PATH and manpage for it:
**whereis** route
route: /sbin/route /usr/share/man/man8/route.8.gz

Find manpages containing a word:
**apropos** route
NETLINK_ROUTE (7)    - Linux IPv4 routing socket
route (8)            - show / manipulate the IP routing table
routef (8)           - flush routes
routel (8)           - list routes with pretty output format
traceroute6 (8)      - traces path to a network host
traceroute6.iputils (8) - traces path to a network host

Find all filesnames containing a word:
**locate** route
(too long to list)

If you have your own personal binaries or scripts:
mkdir ~/bin (if it does not already exist)
logout of X and log back in, your ~/bin will now be in your $PATH
Put any personal executables or scripts in your ~/bin
You can then run them by filename assuming proper permissions (without path prefix)

PS: How do you disable automatic emicons in posts? ;)

---

### Post by Catlike on 2012-07-04
> **arubislander said:**
> Which only works if the the command is in the %PATH% to begin with (can't decide if the pun was intended or not). Most of the time you'd want to no the file path for a command that's not in the environment path...

Thank you.

Are you saying that I have to know and change directory to the directory in which the desired file resides?

---

### Post by Catlike on 2012-07-04
Thank you.
> **efflandt said:**
> To find a command in your $PATH:
**which** route
/sbin/route
What does *$PATH* mean?
Is the second line (/sbin/route) a suggested possible result of executing "which"?

> **efflandt said:**
> I guess finds a command in $PATH and manpage for it:
**whereis** route
route: /sbin/route /usr/share/man/man8/route.8.gz
What is a manpage? 

> **efflandt said:**
> Find manpages containing a word:
**apropos** route
NETLINK_ROUTE (7)    - Linux IPv4 routing socket
route (8)            - show / manipulate the IP routing table
routef (8)           - flush routes
routel (8)           - list routes with pretty output format
traceroute6 (8)      - traces path to a network host
traceroute6.iputils (8) - traces path to a network host
I don't get the above stuff. Are these modifications to the command "apropos route"? 

Again, thank you.

---

### Post by lolpenguin on 2012-07-04
man stands for manual. A manpage is a manual page. man is a utility for accessing manpages. Useful for quick reference to a program. e.g.
```
man man
man cp
```
The $PATH variable is used to determine where to look for programs by default in a shell.

---

### Post by efflandt on 2012-07-04
The commands were **bold** in my reply and word that followed in those examples (route) was just an example of searching for things related to "route".

There are a bunch of variables in your environment.  To see all of them type: **env**

One of those variables is PATH which lists paths where it looks for commands, programs, scripts, but a $ prefix is need to expand the variable to its value.  And "echo" can echo text strings or variables following it.  Example:

**echo $PATH**
/home/efflandt/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

Anything in that colon separated list of directories that has execute permission can be executed by just its filename, without having to use a path prefix.

To see what apropos does try: **man apropos** (use cursor keys to scroll, or q to quit or exit the manpage)

---

