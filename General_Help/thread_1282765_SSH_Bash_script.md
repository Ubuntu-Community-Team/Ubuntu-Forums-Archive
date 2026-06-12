---
title: "SSH Bash script"
date: 2009-10-04
forum: General Help
---

### Post by Primefalcon on 2009-10-04
I have this script I am trying to get to work and it doesn't seem to be able to work

```
#!/bin/bash
read password
ssh <username@<localIP>
$password
<run a few commands>
exit
```

the problem is, it doesn't seem to be entering the password into the ssh login

I've also tried


```
#!/bin/bash
read password
ssh <username@<localIP>
echo $password
<run a few commands>
exit
```

---

### Post by renkinjutsu on 2009-10-04
it would be impossible for that script to work.. because it'll only execute $password AFTER ssh quits

and after ssh quits, it would say
```
bash: <yourpasswordhere>: command not found
```

read up on `expect`
```
man expect
```

and look for tutorials on the internet

---

### Post by ibuclaw on 2009-10-04
Setup ssh on the server side to allow login using a private key.

change into your ssh directory.
```
cd ~/.ssh
```
and generate a public/private key pair.
```
ssh-keygen -t rsa -b 4096 -f root
```
then transfer the public key to the server, so that it goes into /root/.ssh/authorized_keys

This should do it automatically for you.
```
ssh-copy-id -i ~/.ssh/root.pub root@192.168.1.14
```
Afterwards, any attempt to login to the server from with your username should prompt you once for a password, then use the key to login w/o a password needed from therein.

Also, you are doing ssh all wrong...
The syntax is:
```
ssh name@host command
```
or
```
ssh -X name@host Xcommand
```
for running an X application from the server.

For reading material/reference: [https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Regards
Iain

---

### Post by ermeyers on 2009-10-04
Being a farely old fart, I'm going to mention kermit, from ckermit.  Just because.

---

### Post by Primefalcon on 2009-10-04
I know how to use ssh, I use it every day

ssh johnblow@192.168.1.106 hence ssh username@localip

for an example then I'm logged in there...

I just cant automate the login process, I suppose I could use stdin with echoed pipe.....

damm seems yo cant redirect to stdin damm, I'll check into expect

nvm I got it working managed to set ssh to accept pipe redirected stdin, sweet :-)

---

