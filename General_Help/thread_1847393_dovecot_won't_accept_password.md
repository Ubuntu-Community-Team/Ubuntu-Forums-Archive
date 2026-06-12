---
title: "dovecot won't accept password"
date: 2011-09-20
forum: General Help
---

### Post by AlexBooton on 2011-09-20
Hi,

I'm having a heck of a time trying to get my mail from a Windows client using Outlook.

mail.log says:
dovecot: pop3-login: Disconnected (tried to use disabled plaintext auth): rip=192.168.0.51, lip=192.168.0.189

I've very carefully configured dovecot.conf by following the [Dovecot Basic Configuration Wiki]("http://wiki.dovecot.org/BasicConfiguration")

Here's what I've done so far:
1.  Set "disable_plaintext_auth = no" 
2.  Created /etc/passwd.dovecot with a single line:
  al:{PLAIN}mypassword
3.  Set passdb in the auth default section of dovecot.conf

Here's what dovecot -n says in total:
   ```

# 1.2.15: /etc/dovecot/dovecot.conf
# OS: Linux 2.6.38-11-generic i686 Ubuntu 11.04
disable_plaintext_auth: no
login_dir: /var/run/dovecot/login
login_executable: /usr/lib/dovecot/imap-login
mbox_write_locks: fcntl dotlock
auth default:
  passdb:
    driver: passwd-file
    args: /etc/passwd.dovecot
  userdb:
    driver: passwd

```

As far as I can see, I've done everything required.  But I guess not.

What am I missing?

Any suggestions greatly appreciated.

---

### Post by patryk77 on 2011-09-20
Just to be sure, you *did* restart dovecot after changing the config file? 

sudo service dovecot restart
or sudo /etc/init.d/dovecot restart

---

### Post by AlexBooton on 2011-09-20
> **patryk77 said:**
> Just to be sure, you *did* restart dovecot after changing the config file? 

sudo service dovecot restart
or sudo /etc/init.d/dovecot restart

Hi,

Not sure what this all means but here's what I get:

This happens whenever I try dovecot restart
```
root@pti-server:/home/ed# sudo service dovecot restart
restart: Unknown instance:

```

Here's /etc/init.d/dovecot restart
```
root@pti-server:/home/ed# sudo /etc/init.d/dovecot restart
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service dovecot restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) and then start(8) utilities,
e.g. stop dovecot ; start dovecot. The restart(8) utility is also available.
dovecot start/running, process 3229

```

And finally:
```

root@pti-server:/home/ed# restart dovecot
restart: Unknown instance:

```

More weirdness:
ps -A does NOT give the same pid's as above (see 3229 above)  
```
root@pti-server:/home/ed# ps -A | grep dovecot
 2866 ?        00:00:00 dovecot
 2867 ?        00:00:00 dovecot-auth

```

I don't know what this all means and why restart NEVER works.

But I do think dovecot is running and the snippet from the mail log in my first post seems to confirm that.  

It just doesn't work! ;)

---

### Post by AlexBooton on 2011-09-20
I'm now getting a different message in mail.log.

Maybe I've now got dovecot running where, perhaps, it wasn't before.

Here's the message:
```
dovecot: auth(default): passwd-file /etc/passwd.dovecot: User ed is missing userdb info
```

And here's my /etc/passwd.dovecot:
```
# cat /etc/passwd.dovecot
ed:{PLAIN}mypassword

```

There's only one line in the file.  The only change I made was to substitute "mypassword" for my real p/w.

I copied the format of the file from the dovecot wiki.  Is there  an error in the file?

I've googled for that error message and found nothing useful.

Any ideas?

Thanks

---

### Post by AlexBooton on 2011-09-21
Anyone?

I'm desperate.

Any/all ideas gratefully accepted.

---

### Post by patryk77 on 2011-09-21
Sounds like you need additional info in your Password file (/etc/passwd.dovecot)

[http://wiki.dovecot.org/AuthDatabase/PasswdFile](http://wiki.dovecot.org/AuthDatabase/PasswdFile)

I think you need at least the guid/uid, though I never used dovecot with a passwd file myself, so I am no expert :P

---

### Post by AlexBooton on 2011-09-21
> **patryk77 said:**
> Sounds like you need additional info in your Password file (/etc/passwd.dovecot)

[http://wiki.dovecot.org/AuthDatabase/PasswdFile](http://wiki.dovecot.org/AuthDatabase/PasswdFile)


Thanks for the feedback.  If I read the site you referenced correctly, the extra stuff in the password file is un-needed:

```
For a password database it's enough to have only 
the user and password fields. For a user database, 
you need to set also uid, gid and preferably also 
home (see VirtualUsers). (gecos) and (shell) fields 
are unused by Dovecot. 
```

I've been using this reference: [http://wiki.dovecot.org/BasicConfiguration]("http://wiki.dovecot.org/BasicConfiguration") where the contents of the p/w file are shown as: 

$USER:{PLAIN}password

Since I'm trying to use plaintext passwords, the above ought to work (I think :))

But, I tried it anyway.  My user and group id's are both 1000 (I'm the first user).  So now here's my /etc/passwd.dovecot:

```
ed:{PLAIN}<mypassword>:1000:1000::/home/ed:::
```

But it still doesn't work.

I know this works for others. Something is screwy with my setup.

---

