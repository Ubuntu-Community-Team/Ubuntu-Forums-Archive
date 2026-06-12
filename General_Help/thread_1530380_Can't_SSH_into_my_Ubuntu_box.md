---
title: "Can't SSH into my Ubuntu box"
date: 2010-07-13
forum: General Help
---

### Post by Chromisdesigns on 2010-07-13
I'm having problems getting openssh server to accept connections in Ubuntu 10.04
 
Here's what I've done (twice): 
 
Installed Ubuntu 10.04 on USB drive with pendrive installer. This creates a default user "ubuntu" and you don't get the chance to choose a password for it. 
 
Started a keyring for network access and selected password. Works. 
 
Enabled VNC and selected password. Works fine with VNC client on local network. Logs in as "ubuntu" user and asks for the VNC password, then connects. Note: the client doesn't know the "ubuntu" user password, and neither do I! However, it works.
 
Installed openssh client and server from Ubuntu s/w center. 
 
$ ssh localhost OR $ ssh ubuntu@localhost try to connect, but asks for password, which I don't know (see step one, above) 
 
so, then I created a new user, with known password, logged in as new user in Ubuntu, works. 
 
however, $ ssh newuser@localhost still fails, even when correct password for <newuser> is supplied. Rejects the password three times, then gets the usual error about keys. 
 
I also tried connecting with an SSH terminal app from my iPad, again using <newuser>. It gets essentially the same error, "failure to authenticate".
 
All this is still on my own LAN, haven't gotten to going outside the router yet.
 
Anyone have any suggestions at this point? 
 
What I want to do in the end is use VNC over SSH from a client on my iPad to talk securely to Ubuntu while I'm traveling.
 
Regards,
 
Bob

---

### Post by s.fox on 2010-07-13
Hello and welcome to the forum,

Out of curiosity does the following work?

```
ssh newuser@127.0.0.1 
```Just thinking something odd may be in your hosts file.

-Silver Fox

---

### Post by Chromisdesigns on 2010-07-13
> **Silver_fox_ said:**
> Hello and welcome to the forum,

Out of curiosity does the following work?

```
ssh newuser@127.0.0.1 
```Just thinking something odd may be in your hosts file.

-Silver Fox

Nope, neither that nor ssh newuser@10.0.0.7  (which is IP of Ubuntu on my lan) work.  Both get  the "host key could not be verified, do you want to continue anyway" message, when answered "yes" it adds the ip address to hosts file, then goes into the password dialog and refuses the connection, same as before with other alternatives.

Someone in another forum suggested checking AllowUsers section of /etc/ssh/sshd_config --

I did that, but there is NO such section in either ssh_config or sshd_config.  Should there be?  If so, do you know the correct syntax for the entry?

Here is what the auth log shows for the connection attempts. Apparently thinks it's an invalid user!??? (I replaced actual user id in this post with "**dummy user name**")

Jul 13 19:20:28 ubuntu sshd[3974]: Invalid user **dummy user name**  from 127.0.0.1
Jul 13 19:20:28 ubuntu sshd[3974]: Failed none for invalid user **dummy user name**  from 127.0.0.1 port 34240 ssh2
Jul 13 19:20:50 ubuntu sshd[3974]: pam_unix(sshd:auth): check pass; user unknown
Jul 13 19:20:50 ubuntu sshd[3974]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=localhost 


Thanks,

Bob

---

### Post by ibuclaw on 2010-07-13
> **Chromisdesigns said:**
> Nope, neither that nor ssh newuser@10.0.0.7  (which is IP of Ubuntu on my lan) work.  Both get  the "host key could not be verified, do you want to continue anyway" message, when answered "yes" it adds the ip address to hosts file, then goes into the password dialog and refuses the connection, same as before with other alternatives.

Someone in another forum suggested checking AllowUsers section of /etc/ssh/sshd_config --

I did that, but there is NO such section in either ssh_config or sshd_config.  Should there be?  If so, do you know the correct syntax for the entry?

/etc/ssh/sshd_config should be installed along with the openssh-server package on Ubuntu. If it isn't there, I'd consider a reinstall of it first. :)

---

### Post by Chromisdesigns on 2010-07-13
Well, the plot thickens...

Successful in logging in via ssh (sorta) -- here's what I did:

Just for grins, I changed users from the default "ubuntu" to my new user.  THEN I did ssh localhost...

Asks for the password after the host authenticity key message, passwd entered, bam, I'm in!

However, the other forms of ssh login continue to fail.

ssh newuser@localhost  ssh newuser@10.0.0.7  and sshnewuser@127.0.0.1 all fail the same as before

Here's the log entries for the successful ssh localhost, and the others

Jul 13 19:46:06 ubuntu sshd[4474]: pam_sm_authenticate: Called
Jul 13 19:46:06 ubuntu sshd[4474]: pam_sm_authenticate: username = [dummy user]
Jul 13 19:46:06 ubuntu sshd[4474]: Accepted password for dummy user from 127.0.0.1 port 51302 ssh2
Jul 13 19:46:06 ubuntu sshd[4474]: pam_unix(sshd:session): session opened for user dummy user  by (uid=0)
Jul 13 19:51:18 ubuntu sshd[4539]: Received disconnect from 127.0.0.1: 11: disconnected by user
Jul 13 19:51:18 ubuntu sshd[4474]: pam_unix(sshd:session): session closed for user dummy user
Jul 13 19:51:44 ubuntu sshd[4661]: Invalid user dummy user from 10.0.0.7
Jul 13 19:51:44 ubuntu sshd[4661]: Failed none for invalid user dummy user from 10.0.0.7 port 34421 ssh2

SSH terminal app on another machine still can't get in, either.

So what's going on here?  Any ideas, guys?

Thanks,

Bob

---

### Post by Chromisdesigns on 2010-07-13
> **ibuclaw said:**
> /etc/ssh/sshd_config should be installed along with the openssh-server package on Ubuntu. If it isn't there, I'd consider a reinstall of it first. :)

/etc/ssh/sshd_config IS there, there is just no "AllowUsers" section in it.  I'm told in another forum it's not necessary, and the default if missing is "All".

---

### Post by Chromisdesigns on 2010-07-13
Bump.  Tried a bunch of suggestions, still the only way I can get logged in with SSH is if I do the following:

ssh username@localhost   AND already logged in with same username on the local machine

All other tries fail.

Any more suggestions?

Thanks,

Bob

---

### Post by Chromisdesigns on 2010-07-14
OK, things are improving a bit.  I now have it to where I can login, either from the  localhost or from a remote client, using SSH, but it only works if I login as the same user as is currently logged in locally.

In other words, if I am logged in locally as userguy, a remote login using SSH works fine, once I supply userguy's password.

However, if I try to login as otheruserguy, no matter what I do, it refuses the connection, even when I supply the correct password for otheruserguy. (unless, of course, I go back to the linux machine and login locally as "otheruserguy" first.)

This is true whether the connection attempt is made on the localhost machiine, or remotely via a client on another machine on my Lan. (I haven't set up the firewall yet to allow access from outside, but that should be a piece of cake compared to what this involved!).

Is this the way it's supposed to work, out of the box?  

I can probably live with it this way, for what I need to do, but surely there must be a way to configure SSH to allow multiple users to connect, regardless of who is logged in locally at the time???

Regards,

Bob

---

### Post by Chromisdesigns on 2010-07-15
Bump.
 
Discussion has moved to this thread in security forum:
 
[http://ubuntuforums.org/showthread.php?t=1530694](http://ubuntuforums.org/showthread.php?t=1530694)
 
Would still appreciate any further insights.

---

### Post by Chromisdesigns on 2010-07-18
Problem fixed.  Turned out to be an issue with username vs short user name.  If they are different, SSH fails.  If they are the same, SSH works.  

Wierd!

---

### Post by untitledtv on 2011-10-29
Can you clarify what that means, I am having the same problem.  What do you mean by short name?

---

