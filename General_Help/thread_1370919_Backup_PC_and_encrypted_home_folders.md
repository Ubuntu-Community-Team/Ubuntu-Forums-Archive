---
title: "Backup PC and encrypted home folders"
date: 2010-01-02
forum: General Help
---

### Post by calucifer on 2010-01-02
Hi, I'm recently switched my work laptop from running winXP to runing karmic. 
I'm still at the stage of getting my various bits and bobs working correctly. One of these I (may) have a problem with is backup's. 
I've ran backuppc on a ubuntu 9.04 box in the attic for the last year or so and I've been backing up my laptop to that. But since the switch, since I have an encrypted home dir, what is being backed up is the encrypted files.
First, can I recover these if needed (I kept a copy of my passphrase), or can I get backuppc to ssh in as me with my home dir mounted correctly?

Backuppc is using rsync over ssh

I've been using linux on and off since about redhat 5.0, so I'm not afraid of the command line or vi

Any help or advise appreciated

---

### Post by smoka on 2010-01-22
I'm just thinking exactly the same thing, and I suppose there's a few ways of doing this that I can think of:

- rsync the encrypted home directory from the laptop/pc to say another location on the server that will then be backed up (easy, but possible security issue)

- Backup the actual encrypted home folder (looks like this could be a bit of a pain to recover though - [http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/](http://www.kaijanmaki.net/blog/2009/10/26/recovering-files-from-ecryptfs-encrypted-home/) )

- As you suggested - set up another backup job logging in as the user with the encrypted directory (should work, but I haven't tested yet)

If anyone else has got any good suggestions, I'm all ears too.

---

### Post by calucifer on 2010-01-23
In the end I went with setting the backup user to my account, which ssh's in and decrypts my home folder, it then runs the (sudo'd) backup's.
Obviously this wouldn't really work if you had more than one home folder to backup. But I have only one, so I'm sorted :D

---

### Post by itismike on 2010-11-06
A solution to this conundrum continues to elude me. If I use BackupPC to backup my data using the default 'root' account, my home folder data will be encrypted, and I, as a user,  will be unable to browse the backed-up files to restore them. The same holds true if I create a user named backuppc on my client and give it necessary permissions.

If I backup the data as a like-named user from the BackupPC server, I could browse my files and perform a restore, but it would be impossible to backup any system files/folders owned by root with permissions of 770 or higher because my username doesn't have read-access to them.

A possible solution is to use two separate jobs: backup my user folder with a like-named user account on the server, and then backup the system folders (/etc, /var, etc.) using a root account, but it doesn't appear possible to add more than one host/username combination to BackupPC.

Does anyone have a good (and secure) solution to backing up encrypted home folders?

---

### Post by czr114 on 2010-11-07
If the computer is being used by you and you alone, you'll find full disk encryption to be less troublesome than home folder encryption. The only situation in which it might not be appropriate is on older hardware.

---

### Post by itismike on 2010-11-07
thanks for the reply, czr114, but my setup is a bit more complicated than that. I am interested in a solution using BackupPC for home and system folders that would be suitable in an enterprise environment.

---

