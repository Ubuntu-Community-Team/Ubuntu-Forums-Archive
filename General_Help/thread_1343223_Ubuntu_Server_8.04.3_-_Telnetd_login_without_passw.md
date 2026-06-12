---
title: "Ubuntu Server 8.04.3 - Telnetd login without password"
date: 2009-12-01
forum: General Help
---

### Post by T Bag on 2009-12-01
I know telnet is old and busted, but I'm currently moving my company's software from one OS to Ubuntu.  We currently use telnet and have some logins that don't require a password.  

So, using telnetd in Ubuntu Server 8.04.3, how can I setup a user with no password and have the ability to login via telnet without being prompted for a password?

---

### Post by dcstar on 2009-12-02
> **T Bag said:**
> I know telnet is old and busted, but I'm currently moving my company's software from one OS to Ubuntu.  We currently use telnet and have some logins that don't require a password.  

So, using telnetd in Ubuntu Server 8.04.3, how can I setup a user with no password and have the ability to login via telnet without being prompted for a password?

telnet is just like any other application, it uses whatever password you have for the user account.

Most modern systems will not allow blank passwords for obvious security reasons, but you can manually set blank passwords - just do a web search.

---

### Post by T Bag on 2009-12-02
Even with a blank password I am still prompted for a password when logging in via telnet.  And when one is not entered access is denied.

---

### Post by memilanuk on 2009-12-02
Since I don't have a machine with telnetd setup, much less one with no password (my condolences!) I can't test anything out to help you directly... but have you tried a google search for 'linux telnet no password'?  There are a couple returns that look as if they might have some promise.

HTH,

Monte

---

### Post by T Bag on 2009-12-03
I've done a lot of *googling*, and I haven't come up with much.  Somethings say to remove the password entry in /etc/passwd and others say in /etc/shadow.  After doing either one I'm still prompted for a password in telnet and can't login.  

I believe this might be fixed in the PAM authentication, but I know very little about this.  I'm trying to figure it out, but I can't find any good solid info regarding how programs/daemons use it.  I've looked into the "login" program telnet calls for authentication and can't seem to figure it out either.
  
I'm sure this is something simple that I'm just not aware of yet.

If anybody has any info, or is in the same boat drop me a line.  We can compare notes or at least vent in frustration.

---

### Post by zman121 on 2009-12-03
Well, I generally recommend against telnetd -- its security is nonexistent.
If you really want your system hacked, and you must use telnetd, 

man .rhosts

But -- this is a terrible solution. . . 

I recommend sshd, and if you must, the use of shared keys.  See, for example, 

[http://michael.susens-schurter.com/blog/2008/03/19/easy-rsync-remote-backups-using-ssh-keys/comment-page-1/](http://michael.susens-schurter.com/blog/2008/03/19/easy-rsync-remote-backups-using-ssh-keys/comment-page-1/)

The example in question is using rsync to keep files copied, but if you generate and place the keys, the passwordless login from ssh will work as well.  Instead of using rsync to test the connection to the foreign host, use

ssh NAME_OF_FOREIGN_HOST

instead.

---

