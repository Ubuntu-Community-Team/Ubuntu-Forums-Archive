---
title: "ssh Permission denied (publickey) Bind to port 22 on 0.0.0.0 failed: Address already"
date: 2011-07-19
forum: General Help
---

### Post by neridaj on 2011-07-19
Hello,

I'm trying to add a key public key for my dev box which is a vm running ubuntu natty, and I am unable to connect via ssh. I've tried rsa and dsa, as well as these commands:

exec ssh-agent bash
ssh-add ~/.ssh/id_rsa
ssh-add ~/.ssh/id_dsa
SSH_AUTH_SOCK=0

I also edited my sshd_config file as follows:

ListenAddress 0.0.0.0
AuthorizedKeysFile      %h/.ssh/authorized_keys

I've tried restarting sshd as well as the system, too.

I think I've found the error by running sudo /usr/sbin/sshd -Dd, but I'm not sure how to fix it:

ebug1: sshd version OpenSSH_5.8p1 Debian-1ubuntu3
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-Dd'
Set /proc/self/oom_score_adj from 0 to -1000
debug1: Bind to port 22 on 0.0.0.0.
Bind to port 22 on 0.0.0.0 failed: Address already in use.
Cannot bind any address.

Thanks for any help.

---

### Post by galvatron408 on 2011-07-25
Before you go and do some fancy ssh stuff, perhaps you should consider the basics.

#1 - make sure password ssh works because if it doesn't work, keys won't either (well, technically you could turn off password auth and keys will still work but you know what i mean)

#2 - generate your keys using ssh-keygen -t rsa (create rsa keys ON THE SERVER)

#3 - Allow ssh-keygen to place it in the default location /home/user/.ssh/

#4 - go in to /home/user/.ssh and run...
ln -s id_rsa.pub authorized_keys (this will link authorized_keys to id_rsa.pub)

#5 - now... run chmod 600 id_rsa.pub (if permissions aren't already 600)
then run chmod 700 .ssh (if permissions aren't already 700 on .ssh dir)

#6 - copy id_rsa on to your client machine (make sure it goes in to /home/user/.ssh and make sure the permissions are like above in #5)

#7 - ssh in to your server to see if it uses the key. if it uses the key, you're on the right path. if it doesn't use the key, look in /var/log/syslog or /var/log/messages or /var/log/secure to see why sshd denied you.

---

### Post by Tpolich on 2011-07-25
> **galvatron408 said:**
> 
#4 - go in to /home/user/.ssh and run...
ln -s id_rsa.pub authorized_keys (this will link authorized_keys to id_rsa.pub)


no reason to do that he might want to add more keys later and any guide he reads will make him screw something up if he does that.

cat id_rsa.pub > authorized_keys 

is what you want

---

### Post by galvatron408 on 2011-07-25
if he wants to add more keys later then....

echo "new keystring" >> authorized_keys

or vi authorized_keys
o
<paste key string>
:wq!

whats the problem? he's working on a server. he's a big boy. he knows what he is doing.

---

