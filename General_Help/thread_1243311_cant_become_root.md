---
title: "cant become root"
date: 2009-08-18
forum: General Help
---

### Post by nipunreddevil on 2009-08-18
i use ubutnu 9.04 installed it with wubi.when i run su - and enter my password it says authentication failure.However i using the same password with sudo works.whats the solution

---

### Post by nikhilk on 2009-08-18
> **nipunreddevil said:**
> i use ubutnu 9.04 installed it with wubi.when i run su - and enter my password it says authentication failure.However i using the same password with sudo works.whats the solution

Does running the following command give you a root prompt?
```
sudo su
```

---

### Post by wojox on 2009-08-18
Run sudo it's safer. You should not run directly as root. Your not ready yet. I say this because your answer is right in front of you.

---

### Post by ppirilla on 2009-08-18
The official solution in Ubuntu is to use sudo or gksudo for any command that needs root access.

There are workarounds to get to a root shell, but I have been informed that it is the policy of the Ubuntu Forums not to allow such discussions here.  90% of users are better off just using sudo, anyway.

---

### Post by nipunreddevil on 2009-08-18
> **nikhilk said:**
> Does running the following command give you a root prompt?
```
sudo su
```
nipun@ubuntu:~$ sudo su
[sudo] password for nipun: 
root@ubuntu:/home/nipun# 

this is what i get
guess now i am the root.Why is generally recomended to use sudo only?

---

### Post by Stoneface on 2009-08-18
@ [http://www.stearns.org/doc/sudo.current.html](http://www.stearns.org/doc/sudo.current.html) I found a nice explanation: > X as a non-root user

Here's the first mistake most people make; we start out running X Windows as the root user. Suddenly everything becomes simple; one has immediate access to all files, system administration tasks become easy, one can install new apps, etc.

Here's the problem; a lot of programs shouldn't be run as root. If you start up a file manager as yourself and choose to delete /home, well, your own files will disappear and you'll be cursing yourself all the way to the drawer with the backup tapes. Everyone else's files will still be there. If you did the same thing with the file manager running as root, you'll be staring at a lynch mob very quickly. See my "Undeleting files with MC" article if you don't believe it can happen.

File sharing programs, too, shouldn't be run as root either. If someone exploits a hole in an Irc or Gnutella client, the worst they'll be able to do is work with the files you own. Run them as root suddenly everyone's files are completely open to their view, including the all-important /etc/shadow password file and your coworkers personal email files. Not good.

Do yourself a favor. Run X under your own account, and use the following tips as ways to handle all the tasks that need to be run as root.
su and su - ...................

---

### Post by am256 on 2009-08-18
> guess now i am the root.Why is generally recomended to use sudo only? 	

The forum guidelines suggest using the code in the terminal sudo (superuser do) rather than using a workaround to a root shell. (1) too dangerous for most users (2) if you don't know how to get to a root shell, you probably don't need to (3) MOST ALL issues that require root authorization can be resolved using the sudo command.

Do yourself a favor, use the terminal sudo command, and don't screw up your system.

---

### Post by nikhilk on 2009-08-18
> **nipunreddevil said:**
> this is what i get
guess now i am the root.Why is generally recomended to use sudo only?

Yes you have a root shell now, notice how the prompt changed from a '$' to a '#'.

It is generally recommended to run only specific commands as sudo instead of opening a persistent root shell because you have unlimited power as root and you can damage your system by mistake.
So reduce the risk of damaging your system, run only specific commands that require root privileges via sudo vs using a root shell. And I would say this is not limited only to "new/inexperienced" users, it is a general guideline that applies to all users, experienced or otherwise.

---

### Post by mcduck on 2009-08-18
> **nipunreddevil said:**
> nipun@ubuntu:~$ sudo su
[sudo] password for nipun: 
root@ubuntu:/home/nipun# 

this is what i get
guess now i am the root.Why is generally recomended to use sudo only?

"su" requires the target user's password, so if you wanted to su to root you'd need root's password.

"sudo" uses current user's password.

(and the best way to start a root session in terminal is to run "sudo -i". This loads root's environment variables correctly, while "sudo su" or "sudo -s" don't. )

---

### Post by Commander_Keen on 2009-08-18
that's very interesting.. I did not know that.
thank you.

---

### Post by bilkulbekar on 2009-08-18
try this..

$ sudo bash

it wil open the root account..

type

$ passwd

change your pasword

and use this password in future to log into root account.

---

### Post by mcduck on 2009-08-18
> **bilkulbekar said:**
> try this..

$ sudo bash

it wil open the root account..

type

$ passwd

change your pasword

and use this password in future to log into root account.

Just in case you didn't know, the forum rules forbid instructions for enabling root account.

Ubuntu's security model uses "sudo" instead of root, and the support on these forums is based on that security policy.

Anybody who really needs it will know how to do it anyway, or is at least capable of finding the instructions with Google. On the other hand people enabling root without proper knowledge makes giving any support on these forums considerably harder, not to mention that very few users really need normal root account and pretty much just shoot themselves in the leg by enabling it.

---

