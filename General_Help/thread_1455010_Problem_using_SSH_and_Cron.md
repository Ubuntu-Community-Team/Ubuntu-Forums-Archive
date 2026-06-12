---
title: "Problem using SSH and Cron"
date: 2010-04-15
forum: General Help
---

### Post by Yadda on 2010-04-15
I am attempting to automate a script that executes commands on remote machines via ssh. I have public key authentication setup between the machines using ssh-agent. The script runs fine when executed from the command prompt. I suspect my problem is that cron isn't starting the ssh-agent due to it's minimalist environment. Here is the output when I add the -v flag to ssh:

```

debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: gssapi-with-mic
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: Next authentication method: publickey
debug1: Offering public key: /home/<user>/.ssh/id_rsa
debug1: Server accepts key: pkalg ssh-rsa blen 149
debug1: PEM_read_PrivateKey failed
debug1: read PEM private key done: type <unknown>
debug1: Trying private key: /home/<user>/.ssh/id_dsa
debug1: Next authentication method: password
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
Permission denied, please try again.
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
Permission denied, please try again.
debug1: Authentications that can continue: publickey,gssapi-with-mic,password
debug1: No more authentication methods to try.
Permission denied (publickey,gssapi-with-mic,password).

```

How can I make this work? Thanks!

---

### Post by Yadda on 2010-04-15
starting the ssh-agent in the script before making the call to ssh did the trick.

---

