---
title: "Program to *move* files via SSH over network?"
date: 2009-10-23
forum: General Help
---

### Post by rdd37 on 2009-10-23
Hi all,

This is not an important issue, but I'm wondering if there are any applications that I can use to *move* a file from one system to another, over the network, using SSH. I use WinSCP on my Windows system at work to do this with the F6 ('move') command. What this does (I'm guessing) is copy the file, then remove the local copy.

On Ubuntu, use gftp and sftp (command-line) regularly to transfer files via SSH, but it bothers me (slightly) to have to remember to delete the local copies when I'm finished transferring. (I hate ending up with duplicate files)

I don't believe I can use the nautilus SSH connection option because I have public key authentication set up, and there doesn't seem to be an option to point at my identity file in the UI. 
I've also used scp a few times in the past, but don't believe this can move rather than copy.


Any suggestions?

---

### Post by Bachstelze on 2009-10-23
scp is what you want. For example:

```
scp file host:~ && rm file
```

would copy a file over SSH to your home forlder on host, and delete the local file if the copy was successful.

---

### Post by rdd37 on 2009-10-23
> **Bachstelze said:**
> scp is what you want. For example:

```
scp file host:~ && rm file
```

would copy a file over SSH to your home forlder on host, and delete the local file if the copy was successful.

That certainly is nice & simple. 
It is not absolutely ideal since I have to re-authenticate every time I want to transfer a file (as opposed to leaving sftp client window open & authentication), but it works!

Thank you very much.

---

### Post by Bachstelze on 2009-10-23
> **rdd37 said:**
> That certainly is nice & simple. 
It is not absolutely ideal since I have to re-authenticate every time I want to transfer a file (as opposed to leaving sftp client window open & authentication), but it works!

Since you're using public key authentication, have a look at [ssh-agent]("http://www.securityfocus.com/infocus/1812").

---

### Post by tubasoldier on 2009-10-23
In Gnome you can connect to an SSH server graphically and use it as if it is a filesystem on your own computer, just slower.

I don't have Gnome installed currently but if I remember right it is under:
Places --> Connect to Server

Select ssh and put in the information. A link will show up on your desktop as if it were a disk. Then you can drag and drop to your hearts content

---

### Post by macason on 2009-10-23
If you want to move multiple files with only 1 authentication you can send a directory structure "scp -r" or tar the files up and send the tar, zip it as well if there is lots and you might just save time.

---

### Post by rdd37 on 2009-10-26
Bachstelze - ssh-agent looks interesting. I'll have to read up on it to understand better, but it looks like it could be a very helpful solution.

tubasoldier - unfortunately I don't think there is an option for public key authentication in the Gnome SSH browser, otherwise that would be ideal.

macason - thanks for the info - I'll keep that in mind. unfortunately most of the time I want to put individual files in different directories, but nonetheless this could be helpful at times.


thanks again for all of the responses.. greatly appreciated.

---

### Post by Lars Noodén on 2009-10-27
Try also [filezilla](http://manpages.ubuntu.com/manpages/karmic/en/man1/filezilla.1.html).

---

### Post by rdd37 on 2009-10-27
> **Lars Noodén said:**
> Try also [filezilla](http://manpages.ubuntu.com/manpages/karmic/en/man1/filezilla.1.html).

alas:
"password-protected files are not yet supported"

(regarding public key authentication identity file)

Thank you, though.

---

### Post by Lars Noodén on 2009-10-27
Ok.  [sshfs](http://linux.die.net/man/1/sshfs) then.

That works with public key authentication and you can use your favorite file manager on top of it.

```

# make a mount point to which you have write access
mkdir /home/rdd37/fuse

# connect using a key
sshfs \
 -o ssh_command="ssh -i /home/rdd37/.ssh/sonata.key.rsa -l rdd37" \
 remotehost.example.org:/home/rdd37 /home/rdd37/fuse 

```

As to how the file manager chooses to move or copy the file, you have to set that yourself AFAIK.

---

### Post by rdd37 on 2009-10-27
> **Lars Noodén said:**
> Ok.  [sshfs](http://linux.die.net/man/1/sshfs) then.

That works with public key authentication and you can use your favorite file manager on top of it.



Awesome. I'll have to read up on this and test somewhere first, but it sounds perfect. Thanks so much.

---

