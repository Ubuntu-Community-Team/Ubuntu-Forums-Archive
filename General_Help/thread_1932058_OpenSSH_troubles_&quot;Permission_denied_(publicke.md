---
title: "OpenSSH troubles: &quot;Permission denied (publickey)&quot;"
date: 2012-02-26
forum: General Help
---

### Post by SuaSwe on 2012-02-26
Hi all!

I've just set up a CentOS server, to which I'm trying to configure SSH keypair access from my Ubuntu computer. Unfortunately, it keeps failing with errors such as 'Permission denied (publickey,gssapi-keyex,gssapi-with-mic)' - it's only publickey I'm troubled by as I take it this refers to RSA/DSA keypair authentication.

Process carried out:

- Generated key by 'ssh-keygen -t rsa'
- Copied content of CLIENT:/home/user1/.ssh/id_rsa.pub to SERVER:/home/user1/.ssh/authorized_keys
- Ensured .ssh dirs on both sides are owned by user1 (ls -la output below)

```

[user1@SERVER user1]$ ls -la /home/user1/ | grep ssh
drwx------. 2 user1 user1 4096 Feb 26 22:58 .ssh

[user1@SERVER user1]$ ls -la /home/user1/.ssh
total 12
drwx------. 2 user1 user1 4096 Feb 26 22:58 .
drwx------. 3 user1 user1 4096 Feb 26 22:38 ..
-rw-------. 1 user1 user1  395 Feb 26 22:58 authorized_keys

user1@CLIENT:~$ ls -la | grep ssh
drwx------  2 user1 user1   4096 Feb 26 23:05 .ssh

user1@CLIENT:~$ ls -la .ssh/
total 16
drwx------  2 user1 user1 4096 Feb 26 23:05 .
drwxr-xr-x 30 user1 user1 4096 Feb 26 23:05 ..
-rw-------  1 user1 user1 1766 Feb 26 23:05 id_rsa
-rw-------  1 user1 user1  395 Feb 26 23:05 id_rsa.pub

```

- Edited PasswordAuthentication line in /etc/ssh/sshd_config to "PasswordAuthentication no" to force RSA auth
- Checked that RSAAuthentication is enabled
- Restarted sshd on server by '/etc/init.d/sshd restart' (and 'service sshd restart' - same effect far as I know!)

And still I'm getting "Permission denied (publickey). I've also tried the above process with id_dsa, with the same effect. Password authentication works so long as it's enabled in sshd_config.

I'm pretty lost as to how to proceed from here! Have attached the full 'ssh -vvv' error; the last bit, where it fails, is below - the only "error" I can see is "Roaming not allowed by server"; otherwise it looks to me like the key is being sent but no response is received from the server?

user1@acer-lx:~$ ssh user1@192.168.0.130
// omitted
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug2: service_accept: ssh-userauth
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug2: key: /home/user1/.ssh/id_rsa (0xb7ae2820)
debug2: key: /home/user1/.ssh/id_rsa (0xb7ae2f60)
debug2: key: /home/user1/.ssh/id_dsa ((nil))
debug2: key: /home/user1/.ssh/id_ecdsa ((nil))
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic
debug3: start over, passed a different list publickey,gssapi-keyex,gssapi-with-mic
debug3: preferred publickey,keyboard-interactive,password
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/user1/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic
debug1: Offering RSA public key: /home/user1/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-keyex,gssapi-with-mic
debug1: Trying private key: /home/user1/.ssh/id_dsa
debug3: no such identity: /home/user1/.ssh/id_dsa
debug1: Trying private key: /home/user1/.ssh/id_ecdsa
debug3: no such identity: /home/user1/.ssh/id_ecdsa
debug2: we did not send a packet, disable method
debug1: No more authentication methods to try.
Permission denied (publickey,gssapi-keyex,gssapi-with-mic).
[/code]

---

### Post by SuaSwe on 2012-02-26
Hi guys,

I have identified the problem, and it was to do with CentOS rather than Ubuntu in the end (wasn't sure hence posting here first!). CentOS appears to have encrypted my /home folder (even though I remember specifically unticking that option, but hey ho :D) so followed [_this Ubuntu Community OpenSSH post_]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Troubleshooting") and did the following:

```

[root@SERVER~#] mkdir /etc/ssh/user1
[root@SERVER~#] cp /home/user1/.ssh/authorized_keys /etc/ssh/user1/
[root@SERVER~#] chown -R user1:user1 /etc/ssh/user1
[root@SERVER~#] chmod 755 /etc/ssh/user1
[root@SERVER~#] chmod 644 /etc/ssh/user1/authorized_keys
[root@SERVER~#] vi /etc/ssh/sshd_config 

#RSAAuthentication yes
#PubkeyAuthentication yes
# changed .ssh/authorized_keys to /etc/ssh/user1/authorized_keys <<<<<<<
AuthorizedKeysFile      /etc/ssh/user1/authorized_keys
#AuthorizedKeysCommand none
#AuthorizedKeysCommandRunAs nobody

```

And finally, it works!

---

### Post by ricpp87 on 2013-01-24
I was having the exact same issue. While logging with ssh, it was not being able to read ~/.ssh/authorized_keys for a newly created user I was setting up.

I found this stackoverflow thread and help me solve this issue

[http://serverfault.com/questions/321534/public-key-authentication-fails-only-when-sshd-is-daemon](http://serverfault.com/questions/321534/public-key-authentication-fails-only-when-sshd-is-daemon)

The .ssh directory and authorized_keys file had the right permission but were mislabeled to home_root_t

To check if your dirs and files labels do this:

```
$ ls -laZ
```

and then run this to fix

```
$ restorecon -r -vv /home/user/.ssh
```

---

### Post by gopukrishnantec on 2013-04-24
Hi [ 						 							[IMG]http://ubuntuforums.org/customavatars/avatar789466_10.gif[/IMG] 						 					]("http://ubuntuforums.org/member.php?u=789466") 				 				 					 						 	[**[COLOR=#000000]SuaSwe[/COLOR]**]("http://ubuntuforums.org/member.php?u=789466")

You did it !!!!!!!!!!

Thank you so much.... So happy now :)
:guitar::popcorn:

---

