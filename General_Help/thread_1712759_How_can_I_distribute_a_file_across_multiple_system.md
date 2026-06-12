---
title: "How can I distribute a file across multiple systems in a network?"
date: 2011-03-23
forum: General Help
---

### Post by karthick87 on 2011-03-23
I have more than 60 ubuntu systems in my network. I want to copy files from one system to other ubuntu systems. All IP addresses are listed in a text file.
  So what command can I use to complete the task?

---

### Post by risby on 2011-03-23
Sounds like a job for a bash script

a loop over a file containing hostnames or ip addresses
then an rcp or scp command

for host in $(cat machines.txt)
do
  scp sourcefile ${host}:destination 
done

you'll want to distribute the source user's public key into the destination user's ~/.ssh/authorized_keys file first though

---

### Post by Rakeshvijayan on 2011-03-23
risby will you please explane the  procedure with example

---

### Post by karthick87 on 2011-03-23
> **risby said:**
> Sounds like a job for a bash script

a loop over a file containing hostnames or ip addresses
then an rcp or scp command

for host in $(cat machines.txt)
do
  scp sourcefile ${host}:destination 
done

you'll want to distribute the source user's public key into the destination user's ~/.ssh/authorized_keys file first though


Can you give an example?

---

### Post by sikander3786 on 2011-03-24
I think **risby** was talking about file transfer over a SSH connection or so...

How do you want to transfer the files? Samba, NFS or SSH?

How are the PCs configured and connected to each other and do you want to transfer the same file to all other PCs simultaneously or just individuals PCs?

---

### Post by dazman19 on 2011-03-24
IF you are developing the files (writing and changing them over time) The best solution to this problem is to use an SVN AKA subversion
apt-get install subversion 
Set up a repository and then create a cron job to checkout the files if they have been updated using crontab.

Personally i love version control, it can be used much more than just software development, it supports reverting and notes about each release. 

If you are doing this as a one off thing, then yeh go with risby's solution

you will want to use scp (secure copy) 
read the manual its pretty easy, basically scp just copies files over an ssh connection. So if you have ssh open on all the machines you get a list of their IP addresses in a file, read the file in to your script, then execute a scp command to put the file in a writable location on the host. e.g. if you login as /home/username you should have access to that folder and you can push it out.

---

### Post by karthick87 on 2011-03-26
> **sikander3786 said:**
> I think **risby** was talking about file transfer over a SSH connection or so...

How do you want to transfer the files? Samba, NFS or SSH?

How are the PCs configured and connected to each other and do you want to transfer the same file to all other PCs simultaneously or just individuals PCs?

Either Samba or SSH

---

