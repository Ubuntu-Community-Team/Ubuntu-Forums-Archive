---
title: "SSH public/private key way does not work on some machine"
date: 2009-10-17
forum: General Help
---

### Post by Lex Yu on 2009-10-17
Hi,

As the title says, I do successfully configure the public/private key way and implement login without password in some servers, however for some others (one of them is Fedora11), I am always asked to input password in my terminal. 

I am using ubuntu 9.04 on T61. And here is my trace:

[EMAIL="root@laptop:%7E/.ssh"]root@laptop:~/.ssh[/EMAIL]# ssh -vvv 9.xxx.xxx.xxx

....
debug1: Unspecified GSS failure.  Minor code may provide more information


debug2: we did not send a packet, disable method
debug3: authmethod_lookup publickey
debug3: remaining preferred: keyboard-interactive,password
debug3: authmethod_is_enabled publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /root/.ssh/identity
debug3: no such identity: /root/.ssh/identity
debug1: Offering public key: /root/.ssh/id_rsa
debug3: send_pubkey_test
debug2: we sent a publickey packet, wait for reply
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Trying private key: /root/.ssh/id_dsa
debug3: no such identity: /root/.ssh/id_dsa
debug2: we did not send a packet, disable method
debug3: authmethod_lookup password
debug3: remaining preferred: ,password
debug3: authmethod_is_enabled password
debug1: Next authentication method: password
[EMAIL="root@9.xxx.xxx.xxx"]root@9.xxx.xxx.xxx[/EMAIL]'s password: channel 28: open failed: connect failed: A remote host did not respond within the timeout period.

Any comment will be really appreciated.

Thanks in advance!

Lex

---

### Post by AreEK on 2009-10-17
Do you really want to log in as root on the remote machine? Maybe better to log in as a normal user and su to root...

I have experienced similar problems, and the most usual problem is file system rights on .ssh and the files inside.

Try chmod 700 .ssh and chmod 600 .ssh/*

---

### Post by Lex Yu on 2009-10-17
Thanks for reminder! Finally, I found it turned out a SELinux issue....after stopping SELinux, the key based way works!

---

