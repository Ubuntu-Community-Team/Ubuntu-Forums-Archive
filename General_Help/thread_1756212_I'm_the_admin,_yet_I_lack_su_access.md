---
title: "I'm the admin, yet I lack su access?"
date: 2011-05-12
forum: General Help
---

### Post by SirBen on 2011-05-12
I am a recent convert from Windows, and starting to mess about with terminal. When I try to run 'su', and it prompts me for my password, I enter the only password I used setting up Ubuntu 11.04... Yet it tells me "su: Authentication Error"

How would I go about getting root access? Will I have to redo my install?

Thanks in advance!

-Ben

---

### Post by Rasa1111 on 2011-05-12
try > sudo instead

---

### Post by ~Plue on 2011-05-12
> **SirBen said:**
> I am a recent convert from Windows, and starting  to mess about with terminal. When I try to run 'su', and it prompts me  for my password, I enter the only password I used setting up Ubuntu  11.04... Yet it tells me "su: Authentication Error"


Using su directly would propmt you to enter the root user's password  which isn't set in a normal ubuntu install as most things that require root privileges are done using *sudo*. If you want to access a root shell using your password, use *sudo -i *or *sudo su *

Further reading: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by SirBen on 2011-05-12
I thought that su and sudo were different commands though. I can run sudo, is it the same as the root?

Specifically, this is a problem because I am trying to look at my /etc/sudoers.d readme. The error mesasge that comes up when i try to run it is: Could not open the file /etc/sudoers.d/README. You do not have the permissions necessary to open the file.

To be able to view it, would running 'chmod +r README' hurt the file at all?

Thanks.

-Ben

---

### Post by noah++ on 2011-05-12
> **SirBen said:**
> I thought that su and sudo were different commands though. I can run sudo, is it the same as the root?

The command you type after *sudo* is run as root. So you'll issue *sudo cat /etc/sudoers.d readme* to read that file as root. Alternatively, *sudo bash* starts a root shell, which is the equivalent of *su*.

The reason for this is that *su*, with no arguments, elevates you to the root user. The password you must enter is root's password. Well, root's password is scrambled on Ubuntu installations. Good for security. So you use *sudo* instead, which requires (1) you be a sudoer (2) you enter your own password. (If *sudo *works after you enter your password, then you're configured as a sudoer.)

> To be able to view it, would running 'chmod +r README' hurt the file at all?It's best practice not to change permissions on files a package or installer put there for you. There are often good reasons for permissions to be set exactly the way they are. But by making permissions looser,  you won't make your system less secure (only because this is just a README file) and you won't damage anything.

I suggest you just use *sudo*.

---

### Post by SirBen on 2011-05-12
Ah, thank you very much noah++. A wee lightbulb turned on for me :D

Thanks to Rosa and Plue as well, especially for the link for RootSudo. Another step on my Linux journey has now begun :D

-Ben

---

### Post by Wim Sturkenboom on 2011-05-12
It's a bad habit to change permissions of system files; they are there for a reason. And some programs check permissions on files that they use (not on a standard ubuntu install, I think)

Further you can't change the permissions if you're not the owner, so you need sudo to change it anyway ;)

You can combine sudo with any command, also with 'su -'. This can also be bad because one time you will forget that you have root permissions, you will be in the wrong directory and you will issue the wrong command and accidently delete a file that you should not have deleted (it will happen one day or another to all of us).

At least sudo gives a bit of protection (over being root); you normally don't prepend sudo and you will be warned if you try to access something that you're not supposed to access as a normal user. So you start wondering and realize e.g. that your not in your home directory but in a system directory. Being root, it might have rendered your system useless.

---

