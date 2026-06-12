---
title: "openssh fingerprint"
date: 2009-08-08
forum: General Help
---

### Post by mox386 on 2009-08-08
ok so here it goes....

I have openssh-server configured on a machine. it reports a fingerprint.

I have putty well configured on another machine it reports the same fingerprint

I have my hardware firewall all setup, but no matter how i try to connect the two machines via my ip or local ip somehow the damn firewall screws with the fingerprint, even while disconnected from the internet.

right now it is the same damn fingerprint every time (if it changes I understand that it's some kind of spoof). there was a prior fingerprint, but i dont remember what was going on.

how do get this stuff lined up. I got a recommendation from a fedora buddy at work that it's my damn router screwing with me but the router log shows way to much BS

will edit tomorrow with more info. no will edit monday with more info it's the river this weekend

---

### Post by Brandon Williams on 2009-08-08
The fingerprint is content from within the SSH protocol, at the application layer. It's possible that the router is doing something unexpected with the IP address somehow, but I doubt it's doing anything with the SSH fingerprint itself. It doesn't have any way to do that safely.

I don't use putty, so I don't know how to clear a bad key from the known_hosts file on putty. When I have this problem on my ubuntu machine and I know that it's not a spoofing problem, I run this command:
```
ssh-keygen -R <host|ip>
```
The argument after the -R is the hostname or IP address you're trying to connect to. Typically, even if I'm connecting to a hostname, I still have to run it with the IP address, too. This could be the problem for you, too.

---

### Post by mox386 on 2009-08-11
yeah that helps, I fired up one of "the heaters" these old monster machines I have that I only run during the winter. I used a variation of that command and ... nothing.... so I went to the offending machine and asked the heater (same command) bam response.

The meaning of that is that something is wrong with the machine from the start. That's why it gives the wrong fingerprint. That's crazy!! 

The only solution I can come up with is to wipe the whole shibang clean with a new install and see if I can get the same behavior.

I did that and tonight when I get home I'm going to test this thing out.

---

### Post by Brandon Williams on 2009-08-11
If you wipe the machine and reinstall from scratch, you _will_ end up with a different fingerprint since you'll be using new keys on the server.

What gives you the indication that the server is sending the wrong fingerprint? Are you sure that the fingerprint it sends doesn't match its key? On the server, run these two commands:
```
$ ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key.pub
<fingerprint output here>
$ cat /etc/ssh/ssh_host_rsa_key.pub
<full public key output here>
```

The fingerprint sent by the server should match the fingerprint output by ssh-keygen, and the key stored in the ~/.ssh/known_hosts file should match the public key. If the fingerprint sent by the server doesn't match (it will be reported in the output that says there is a problem), I would be quite surprised. It's more likely that the key in the known_hosts file doesn't match, and this problem will not be solved by reinstalling the server.

---

### Post by mox386 on 2009-08-13
ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key.pub

gives the same key as the client has on it's machine (non public on client). I saved the .pub key and replaced it after the new installation, changing the key also has no effect on what the fingerprint is.

So far the only thing that changes the fingerprint is a clean install on the openssh server, not a new key

---

### Post by Brandon Williams on 2009-08-15
On the server, /etc/ssh/ssh_host_rsa_key.pub is the public half of /etc/ssh/ssh_host_rsa_key, also on the server. The client will not have the private half of that key. If you are connecting to the server with ssh V2 (the default), then changing this key on the server will change it's fingerprint. You can change the key with:
```
sudo sh-keygen -q -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa
```
Changing the public key half alone will not change anything about the server. Only changing the private key on the server will change its fingerprint.

You can get apt-get to do all of this for you on the server _without_ reinstalling the whole machine like this:
```
sudo aptitude purge openssh-server
sudo aptitude install openssh-server
```

As I said before, if the problem is that you have a bad key in ~/.ssh/known_hosts in your user account on the client, then changing the key on the server will not help, because you'll still have a bad key in known_hosts on the client.

---

### Post by Brandon Williams on 2009-08-15
When I have this problem in putty, the Security Alert dialog says that if I click Yes, it will updates putty's cache (i.e. known_hosts). If I do that, I go straight to a login prompt, and the next time I connect, I no longer get the warning. Are you saying that you do not see this dialog? Or are you saying that the fingerprint in the dialog does not match the output of this command when run on the server?
```
ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key
```

---

### Post by mox386 on 2009-08-15
yup got it.

The server needs to have both the public and private keys for the fingerprints to match when the client logs on. 

Thanks man!

---

