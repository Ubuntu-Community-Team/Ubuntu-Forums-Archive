---
title: "Configuring SSH-server IDs and Passwords (Ubuntu 9.10)"
date: 2010-04-09
forum: General Help
---

### Post by kp130000 on 2010-04-09
-

---

### Post by cjhabs on 2010-04-09
> **kp130000 said:**
> Hi Fellow Ubuntu Users!

I'm new to Ubuntu (and Linux) and I am loving what I am using (9.10).  This is a very refreshing change from Windows.

I am trying to configure SSH-server on my Ubuntu 9.10 server.  I was able to install SSH using this tutorial: [http://www.jonathanmoeller.com/screed/?p=1165](http://www.jonathanmoeller.com/screed/?p=1165)

I am even able to successfully SSH into my SSH server from another Ubuntu machine.

What I can't seem to figure out is how to configure a password or key for when clients want to SSH into my server.  Does anyone know how to do so (configure the files on the SSH server?) or know where I can find noob-friendly tutorials?  Thank you in advance.

Cheers,
kp

When a user logs in via ssh, they are using the user name on their own system by default. That username needs to match a username on the ssh server.
Alternatively, you can use:
ssh username@remote_hostname
to use a specific user on the ssh server.
In either case, the password required is that of the user on the ssh server.

You don't need to worry about keys as they get created automatically (you will have to worry if they change at either end, but that is not important right now).

---

### Post by kp130000 on 2010-04-09
-

---

### Post by kp130000 on 2010-04-09
-

---

### Post by cjhabs on 2010-04-10
> **kp130000 said:**
> Update:  I was able to delete the key files and allow for SSH from my client to my server again.

Problem:  I can SSH into my server with the server's local host name.  However, I can't SSH into my server with my client's name.  Also, I still don't know how to set up a passphrase to logins.  Any help?

Cheers,
kp

sory - if I had seen this earlier I could have saved you some time.
You can remove the ~/.ssh/known_hosts file to remove all the known keys - or just delete the changed keys from the file to allow logins again - this a a per user file.

As far as setting up a passphrase, I have only ever used that to configure password-less ssh access so I can't speak from experience there, although I can send you info on how I did that once I am back at work and have my notes available.

---

