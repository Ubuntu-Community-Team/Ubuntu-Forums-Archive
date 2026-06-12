---
title: "Restricted SSH Access"
date: 2010-04-14
forum: General Help
---

### Post by Rich78 on 2010-04-14
I'm trying to lock down SSH for a particular user who wants to use my server for some development, so I'm making him a little play area.

Problem is I'm having difficulties locking the account down.

I've implemented bashrc which appears to be what I wanted at first, restricting the user to a user directory of my choice, but I now find that firstly the user can't use cd at all, not even cd to directories within the users home directory.

But also I've found bashrc to be pretty pointless security wise because I can just type sh and then do what ever the hell I want?  Such as cd / and then ls and see everything on the server.

So I'm wondering if anyone has a solution to this for me?

I want the user to be able to make directories and cd into them in their own user area but not cd .. or / out of their user area.

Thanks.

---

### Post by Rich78 on 2010-04-15
anyone?

---

### Post by rossmoore on 2010-04-15
Hey, I've done something similar to sftp access. Not too sure on the specifics for ssh.

Have you heard of chroot? I think this is what you want. You can set something up in your sshd config file to match the user and chroot them. Alternatively you can just ensure the permission on the filesystem are set up such that he can't read or write anywhere you don't want him to.

Here's a link to info on chroot setup:
[http://www.howtoforge.com/chrooted_ssh_howto_debian](http://www.howtoforge.com/chrooted_ssh_howto_debian)

---

### Post by Rich78 on 2010-04-15
Looks perfect, many thanks :)

---

