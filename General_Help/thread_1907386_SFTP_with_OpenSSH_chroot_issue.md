---
title: "SFTP with OpenSSH chroot issue"
date: 2012-01-11
forum: General Help
---

### Post by tg1390 on 2012-01-11
Hey Guys,

I've set up a SFTP server using OpenSSH.  After following a guide online, I set up a group called sftponly and added a user to this group.  I used the Match group switch in the sshd_config file to match the group so that user's in that group could only connect for SFTP sessions.  I set up the chroot to point to "/home/%u".  

I created a user and added it to the sftponly group.  Then I changed the ownership of that user's home directory to root, and changed the home directory to / . 

When I connected using WinSCP I was locked into my home directory (/home/<username>) over SFTP (good!)  but I was not able to create files or directories in that directory (bad!).  

Oddly enough, when I change the ownership back to the user for their home directory, I am no longer able to connect to the system over SFTP.  It gives me a connection refused message.

Can someone explain to me what's going on?  I'm new at this setup so go easy on me :)

Thanks guys

---

### Post by gsgleason on 2012-01-11
maybe try this:

chown root.sftponly /home/whatever
chmod g+rwx /home/whatever

that will make the directory's group (sftponly) able to create files.

---

### Post by Lars Noodén on 2012-01-11
The [chroot directory](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) must be root-owned and not writable by any other user or group.  That can mean a little fiddling with directory structures and permissinso to get what you want working.

---

### Post by gsgleason on 2012-01-11
> **Lars Noodén said:**
> The [chroot directory](http://manpages.ubuntu.com/manpages/oneiric/en/man5/sshd_config.5.html) must be root-owned and not writable by any other user or group.  That can mean a little fiddling with directory structures and permissinso to get what you want working.

Wow.  I didn't know that.  How is a user supposed to create files in a chrooted directory then?

[edit]

[http://www.gossamer-threads.com/lists/openssh/dev/44657](http://www.gossamer-threads.com/lists/openssh/dev/44657) 

> 
Right, this is on purpose. We ban this because allowing a user write
access to a chroot target is dangerously similar to equivalence with
allowing write access to the root of a filesystem.

If you want the default directory that users start in to be writable
then you must create their home directory under the chroot. After
sshd(8) has chrooted to the ChrootDirectory, it will chdir to the
home directory as normal. So, for a passwd line like:

djm:*:1000:1000:Damien Miller:/home/djm:/bin/ksh

Create a home directory "/chroot/djm/home/djm". Make the terminal "djm"
directory user-owned and writable (everything else must be root-owned).
Set "ChrootDirectory /chroot" in /etc/config.

A variant of this that yields less deep directory trees would be to set
the passwd file up as:

djm:*:1000:1000:Damien Miller:/upload:/bin/ksh

Create "/chroot/djm/upload", with "upload" the only user-owned and writable
component.

-d 


---

### Post by Lars Noodén on 2012-01-11
> **gsgleason said:**
> Wow.  I didn't know that.  How is a user supposed to create files in a chrooted directory then?

[edit]

[http://www.gossamer-threads.com/lists/openssh/dev/44657](http://www.gossamer-threads.com/lists/openssh/dev/44657)

You can make subdirectories in the chrooted directory and the user can own/edit them.

---

### Post by tg1390 on 2012-01-11
> **Lars Noodén said:**
> You can make subdirectories in the chrooted directory and the user can own/edit them.

This was the approach that I ended up taking.  I created a directory called upload and changed the owner to sftpusr.  It just seems like a bit of an ugly hack to me.  I'm assuming there isn't a way to redirect down the home directory tree as specifying /home/%u/upload as the chroot directory didn't work for me.

---

### Post by tg1390 on 2012-03-09
Is there anyone who has written a redirection script for the SFTP user to the writeable subdirectory?  I would like to not have to cd when I get on the system.

The script would run when the specified user logs in and would change directories for them.  

I'm still a little green with respect to bash scripting.  Is this feasible?

---

### Post by Lars Noodén on 2012-03-09
> **tg1390 said:**
>  I would like to not have to cd when I get on the system.

You can specify a path when you connect.  That would be one way.

```

sftp tg1390@*sftp.example.org*:/home/tg1390/Public/HTML/

```

It has to be a valid path, though.

---

### Post by tg1390 on 2012-03-09
Unfortunately I have no control how the server is accessed.  I am dealing with a 3rd party who is not willing or able to change the way they access the system.  They expect the directory they land in to be writeable...

I sent them about 3 emails just to make sure they were really saying that they couldn't just cd into the directory, I couldn't believe it myself.

So at this point I'm wondering if it would be easier to move to a different SFTP server because I don't see this working any other way.

---

### Post by tg1390 on 2012-03-14
Anyone got any ideas for this?

---

### Post by Habitual on 2012-03-14
n/m.

Next post...

---

### Post by Habitual on 2012-03-14
Users can NOT write to a directory they have no permission to write to regardless of any sftp software/daemon setting/config.

",...that user's home directory to root..."

glgleason is correct:
```
sudo chown root.sftponly /home/whatever
sudochmod g+rwx /home/whatever
```
or 
sudo chmod 770 /home/whatever
Terminal >
```
ls -ld /home/$user
```

output please.

On a short note, I'd quit messing with permissions if you don't understand them.

---

### Post by tg1390 on 2012-03-14
I got it figured out finally, just needed to change the user's home directory to /uploads.  Where uploads was located at /path/to/chroot/folder/uploads.

Interestingly enough, usermod would not let me do this as it didn't recognize a folder at the path /uploads (because it's not really there). So, I had to edit /etc/passwd directly.

Thanks for the help guys :)

---

