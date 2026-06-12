---
title: "ssh as root for backup"
date: 2009-10-16
forum: General Help
---

### Post by bryanvick on 2009-10-16
I am using rdiff-backup to backup my desktop to a server.  The server initiates the backup nightly via ssh.  

My problem is that the server needs to ssh into the desktop as root so that it has read access to all files that it is backing up.  When I allow the server to ssh in as a regular user, it can't read all files, and thus some files don't get backed up.  All the examples of using rdiff-backup like I am simply have rdiff-backup ssh into the client as root, but since Ubuntu locks the root account, I can't follow the directions at this point.

Should I unlock the root account somehow, or is there a better solution?

---

### Post by Carl Hamlin on 2009-10-16
> **bryanvick said:**
> I am using rdiff-backup to backup my desktop to a server.  The server initiates the backup nightly via ssh.  

My problem is that the server needs to ssh into the desktop as root so that it has read access to all files that it is backing up.  When I allow the server to ssh in as a regular user, it can't read all files, and thus some files don't get backed up.  All the examples of using rdiff-backup like I am simply have rdiff-backup ssh into the client as root, but since Ubuntu locks the root account, I can't follow the directions at this point.

Should I unlock the root account somehow, or is there a better solution?

While it *is* possible to unlock the 'root' credentials in Ubuntu, doing so reduces the security level of your system, and explaining the process is prohibited by the TOS on these forums. If you'd like more information in private, please mail me at [email]tin.cans.and.string@gmail.com[/email].

---

### Post by benj1 on 2009-10-16
i backup using rsync over ssh without problems, but i initiate it client side, why dont you try that.

thinks ....

is that even possible is the ssh-server on your desktop ?

---

### Post by bryanvick on 2009-10-16
I wanted to avoid initiating from the client side, because I want all backup logic to reside on my backup server.  That is where all the reporting/emailing on backup status happens.

I think it would work though as long as I edited the sudoers file to allow my regular user to run rdiff-backup using sudo without having to enter a password, that way I could set it up to run in a script without interaction.

Could I set up a user on my desktop that has access to read all files and use that user?

---

### Post by lavinog on 2009-10-16
client side makes more sense to me also.

Are you backing up your whole desktop or just the home folders?
If just the home folders, you could have the backup run as each user, or create a backup user that belongs to each group...keep in mind the backup user would then have access to everyones files.

---

### Post by bryanvick on 2009-10-16
For now I am just backing up the home folder.  I like the idea of a backup user who is part of each group.  This will fail though for files that are only readable by the owner.

---

### Post by benj1 on 2009-10-16
run it as a cron job, cron runs as root by default.

---

### Post by bryanvick on 2009-10-16
Running it as a root cron job would work if I wanted to initiate the backup from the desktop, but I want to do it from the server.  There are reasons I can't/don't want to initiate from the desktop.

I just unlocked my root account to test that solution.

---

### Post by benj1 on 2009-10-16
true doh

the only option is to enable logging in as root and set up a root account on your desktop, although that brings with it other security problems.

another thought, you say you want to keep it all centralised,why not initiate the ssh tunnel from your desktop, then either run a script held on the server (dont know if that would work) or copy it over to /tmp and execute it from there ?

---

### Post by lavinog on 2009-10-16
Would it be ok a daemon existed on the desktop that polled the existance of a file such as /tmp/startbackup.  when the file is detected the daemon initiates the backup as root to the server, then removes the file.
This way the server is still initiating the backup, but the desktop handles the security.

---

### Post by benj1 on 2009-10-16
its possible i suppose, why do you need the server to be in control of when the backups are done ?

---

### Post by bryanvick on 2009-10-16
The way rdiff-backup works is sort of like lavinog's suggestion.  It opens an ssh tunnel, and starts a service process on the client, then the server communicates w/ that process to pull the data onto the server.

Unlocking the root account seems to have gotten it working.

I want the server to be in control of the backup for a couple of reasons:
1. It is simpler to have one place to administer all backup related activities, instead of having backup logic strewn about the network.  Report and email generation happens on this server so it is easier if all the knowledge of backups sit on this server.
2. The client actually can't initiate communication with the server because it is on a private network.  The server can initiate the communication with the desktop because the desktop has a public ip address.  To have the desktop initiate communication I would have to first open a vpn tunnel.

---

### Post by bodhi.zazen on 2009-10-16
Use ssh keys.

Thsi way you can ssh in as root but still keep the root account locked.

In /etc/ssh/sshd_config change 

> PermitRootLogin without-password

See [http://www.manpagez.com/man/5/sshd_config/](http://www.manpagez.com/man/5/sshd_config/)

---

### Post by lavinog on 2009-10-16
+1 for keys. Especially since the desktop is accessable with the public ip.

---

### Post by bryanvick on 2009-10-16
But to get my public key from the server onto the desktop I need to use:

ssh-copy-id -i <public key of server> root@mydesktop

...which will require that I enter the root's password.  Isn't this correct?

---

### Post by lavinog on 2009-10-16
Only that one time.

---

### Post by bryanvick on 2009-10-16
So I could unlock the root, insert the public key into root's authorized-key file, then lock root with passwd -l root.  That sounds pretty good.

---

### Post by bodhi.zazen on 2009-10-16
> **bryanvick said:**
> But to get my public key from the server onto the desktop I need to use:

ssh-copy-id -i <public key of server> root@mydesktop

...which will require that I enter the root's password.  Isn't this correct?

No, transfer the key to a regualr user account, ssh in as that user, transfer the key with sudo.

```
sudo -i

cat ~user/key > /root.ssh/authroized_keys
```

To be honest , it is not that big a deal, although I advise you lock the root accoutn when you are done :

```
sudo usermod -p '!' root
```

---

### Post by bryanvick on 2009-10-16
What's not that big of a deal?  The root account being unlocked?

---

### Post by bodhi.zazen on 2009-10-16
> **bryanvick said:**
> What's not that big of a deal?  The root account being unlocked?

Unlocking the root account, transferring your ssh key, and re-locking the root account.

---

