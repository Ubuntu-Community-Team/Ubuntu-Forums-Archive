---
title: "OpenSSH does not seem to respond to init.d or configuration"
date: 2011-01-06
forum: General Help
---

### Post by crabpot8 on 2011-01-06
Hey all, 

I just setup Ubuntu 10.04, and immediately installed OpenSSH using synaptic. I edited the /etc/ssh/sshd_config file e.g. no password authentication, non-standard port, etc. Using /etc/init.d/ssh restart I restarted the daemon, and everything worked perfectly. 

However, now it's almost like there is a lock on my service somehow. I edited the config file and added "PrintMotd no" and "Banner none". I killed all my active ssh sessions, restarted, and still saw the motd and the banner. Hmm. I then tried sudo /etc/init.d/ssh stop. The script reported ok, but netstat reported sshd as still listening on the port I had defined. I could still login. 

At this point, I don't know what else to do. I have tried looking at auth.log, I don't see anything funny there. I tried rebooting, and the config changes are (apparently) not loaded, I still see the motd upon ssh login. Any ideas on where to go next would be great - this is a totally clean system so I don't know what I am doing improperly :(

---

### Post by efflandt on 2011-01-07
A clue is /etc/login.defs

> # If defined, file which inhibits all the usual chatter during the login
# sequence.  If a full pathname, then hushed mode will be enabled if the
# user's name or shell are found in the file.  If not a full pathname, then
# hushed mode will be enabled if the file exists in the user's home directory.
#
HUSHLOGIN_FILE    .hushlogin
#HUSHLOGIN_FILE    /etc/hushloginsIf I put my username or just **ssh** in ~/.hushlogin, the only thing that shows when I **ssh localhost** is:

> To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

efflandt@natty-ssd:~$Or you could comment out the 1st HUSHLOGIN_FILE line and uncomment the 2nd one and create /etc/hushlogins and experiment with that.

---

### Post by crabpot8 on 2011-01-07
While that works to hush all login info, I actually would like to see the last login details. The main problem is that the config file doesn't seem to be reload-able. If it was, I could more finely control what I see at login rather than having to use .hushlogin to suppress everything. 

Thanks!

---

### Post by KeyserSoze93 on 2011-01-07
what happens if you delete the contents of /etc/motd and make a blank file called /etc/issue.net (unless you want the motd / issue messages on normal TTY login?)

---

### Post by crabpot8 on 2011-01-07
The Motd gets regenerated (I would presume upon login). Here is what I tried:

```

$ sudo vim /etc/motd
  (clear file, save)
$ cat /etc/motd
$ sudo vim /etc/issue.net
   (clear file, save)
$ cat /etc/issue.net
$ sudo /etc/init.d/ssh reload
 * Reloading OpenBSD Secure Shell server's configuration sshd
   ...done.
$ logout
$ ssh foo@bar.com
Linux (bar) 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Last login: Fri Jan  7 12:44:46 2011 from foobar
$ cat /etc/motd
Linux foo 2.6.32-27-generic-pae #49-Ubuntu SMP Thu Dec 2 00:07:52 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

$ cat /etc/issue.net
$ 

```

I have verified that the PrintMotd is set to no in the config. I was wondering if there are somehow two ssh daemons looking at the same config and understanding it differently?

---

### Post by gmargo on 2011-01-07
The Message-Of-The-Day (/etc/motd) is printed by the login process.

To disable printing the motd, you must edit one or both of these files: **/etc/pam.d/login**, **/etc/pam.d/sshd**. The "login" file applies to local logins; the "sshd" file applies to ssh logins.  Each of those two files has this line:
```

session    optional   pam_motd.so

```If you comment out that line, then the motd will no longer be printed at login.

---

### Post by crabpot8 on 2011-01-07
That did it, thanks!! :D

As a general question, what's the point of the "PrintMotd" configuration line in sshd_config, if that is just being ignored and the lines in /etc/pam.d/sshd are overriding it? 

I've never had this issue before when setting up ssh, is this something resulting from how I have my ssh server setup?

---

### Post by crabpot8 on 2011-01-07
Ah, I think I understand. Both PAM and sshd will attempt to print the message of the day, so I have to turn it off in both locations. I don't know how they keep from printing it twice when they are both turned on

---

