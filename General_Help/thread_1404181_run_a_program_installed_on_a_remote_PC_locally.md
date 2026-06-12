---
title: "run a program installed on a remote PC locally?"
date: 2010-02-11
forum: General Help
---

### Post by mahela007 on 2010-02-11
Is it possible to run a program installed on a remote Ubuntu PC on the local PC? What I'm talking about is different from simply sending the GUI over the network (like X tunelling). I want the program to use the processor of the local machine. Is this possible?
(Here's an example. PC 1 has a fast processor. PC2 has gimp installed on it but has a slow processor. Can PC2 make GIMP run on PC1's processor over the network?)

---

### Post by weblordpepe on 2010-02-11
Well basically what you want is remote access to the files, and then execute those files.

My suggestion would be to mount the remote machine's / directory to somewhere on your local machine (using sshfs to mount the directory), and chroot to it and run GIMP.

Chroot basically executes a program telling it that the / is somewhere else. So if you've got some wacky remote computer's / mounted to say /home/dude/remoteroot and specified that with chroot, Im sure it would work.


Im a thinking though it would be kinda wacky slow. I have NO idea how well it would work. To be honest Im not even sure it would world. chroot is used for things like running different versions of software on the same machine and stuff like that so I dont see why not. Hrm let me test..

OK I just tested it. Yes it works. I got a whole crapload of errors in console but eh who cares yea? It works.

OK step one: Mount the remote computer's / to somewhere on your filesystem. You'll need to be root to do this, and make sure sshfs is installed:

**mkdir /localdirectoryfakeroot**

**sshfs -o allow_other remoteuser@remotecomputer:/ /localdirectoryfakeroot**

**chroot /localdirectoryfakeroot**

Then it'll do some wacky crap. I used the **su** command to ensure I was back to my regular user. Then I typed 'gimp' and my remote computer's gimp loaded.
:)

---

### Post by mahela007 on 2010-02-12
Thanks! (BTW nice use of 'wacky') ;-)
No chance of this working from windows to Ubuntu is there?

---

### Post by weblordpepe on 2010-02-13
Hey man you're welcome.

To windows? Im not sure if I understand your question. Do you want to run Windows programs sitting on a remote machine, using CPU of your local computer?

In that case it's the same deal. Mount the remote computer's C drive or something. Or program files etc. And use wine to execute the .exe file.

Unless you're meaning use the local CPU of a Windows computer to run remote linux programs - well thats a tough one. I'll have to rub my brain a bit for that.

---

### Post by mahela007 on 2010-02-13
I want to run linux programs on a remote windows PC. Yes.. I know I'm asking for the impossible (or am I?) ;-)

---

### Post by weblordpepe on 2010-02-16
Cygwin :)

---

### Post by mahela007 on 2010-02-18
But that's just an X server..

---

### Post by Slim Odds on 2010-02-18
the linux OS runs linux apps
the windows OS runs windows apps

you might use a virtual machine

---

### Post by weblordpepe on 2010-02-18
> **mahela007 said:**
> But that's just an X server..Cygwin is NOT an X server. Its a unix environment for Windows.

And linux runs all sorts of applications. Java, python, bash, perl, C/binary, Windows applications etc. It does this through abstraction. On Linux, running a windows program is just like running a Java or Python program. Its abstracted.


Virtual machine sounds like best idea. And mount the remote machine to you locally.

---

### Post by mahela007 on 2010-02-19
Thanks!

---

