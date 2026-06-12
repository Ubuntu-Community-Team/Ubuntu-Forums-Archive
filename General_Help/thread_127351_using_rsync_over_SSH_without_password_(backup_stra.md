---
title: "using rsync over SSH without password (backup strategy)"
date: 2006-02-08
forum: General Help
---

### Post by sander marechal on 2006-02-08
Hello,

I'm having trouble wrapping my mind around passwordless SSH for use with rsync. What I am trying to achieve sounds simple. I want to run a script everytime I shutdown my PC that will rsync over SSH to copy the entire /home directory from my desktop PC to my server. This is for backup purposes.

Ofcourse, I do not want to have a password to my server sitting in cleartext in that init.d script, so I have been looking into RSA authentication for SSH and into ssh-agent. Here's what I have set up so far:

* generated RSA key pairs for user root on local machine (shutdown script will run as root)
* added the public key on the server for user 'sander'
* ran ssh-add on local machine as root.

After this I did (as root): ssh sander@server. Lo and behold, it logged in without a password. Just what I need for the script. Then I rebooted my cleint PC and tried it again. No cookie. ssh asks for my key's passphrase again after the reboot.

Any idea's on how I should set this up so root@local can ssh to sander@server without a password (in a secure way)? Or am I going about it the wrong way entirely and should I do the /home rsync in a different way?

Note: The rsync script will need to run as root I think, because there are multiple users on my Desktop PC. All their home directories should be rsync'd for backup, not just my own user.

Thank you for any help!

---

### Post by dcstar on 2006-02-08
[QUOTE=sander marechal]
.......
Note: The rsync script will need to run as root I think, because there are multiple users on my Desktop PC. All their home directories should be rsync'd for backup, not just my own user.

Thank you for any help![/QUOTE]
I think you should have a look at: 

man rsyncd.conf

and have a close read of the user authentication stuff.

---

