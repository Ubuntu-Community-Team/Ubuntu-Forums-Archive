---
title: "Parallel I/O port permissions"
date: 2010-06-24
forum: General Help
---

### Post by Cool Javelin on 2010-06-24
Does anyone have any experience with using the parallel port(s) as general I/O port?

I am writing some home automation software and using Free Pascal.

From what I read, if I want to use the parallel port, I first must lock the port using a function call called IOperm (I assume this tells Linux I want exclusive access to the hardware port so no other programs can hose it, which is fine, except...)

Locking the port requires me to be root. I prefer to run the program in a user mode (not root.)

A couple of questions:

#1, (preferred) is there an alternative to reading the hardware directly? can I use a Linux call to read through the OS?

#2, Maybe I can write a second small program to set permissions on the port so my home automation software can run in user mode (not root.)

#3, (not preferred) Can I tell Linux the port doesn't exist (Maybe recompile the OS) so I can have access to it without Linux getting in the way?

#4, maybe a paradigm shift is in order and do it a totally way?

I thought about writing a small (root) program that reads the port and makes a file with the port info that my HA software reads, but that idea doesn't feel right.

Thanks for any help,
Mark.

---

### Post by Cool Javelin on 2010-06-29
OK, How about a different tactic.

I see there are some programs that will accept the root password from the command line like Putty, or other programs that ask for the password when they start like Synaptic Package Manager or sudo.

How can I supply a password on the command line to allow my program to run as root?

Is it necessary I write a small startup script to run it in another shell (supplying the password in the script) or can I get the program to supply the password to the OS directly?

Thanks for the help.

Mark.

---

