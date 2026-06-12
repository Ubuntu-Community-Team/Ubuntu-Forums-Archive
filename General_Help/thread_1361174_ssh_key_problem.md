---
title: "ssh key problem"
date: 2009-12-21
forum: General Help
---

### Post by Neezer on 2009-12-21
I am getting an error when trying to use and rsa key with ssh.

I have a server machine and my laptop both in front of me right now. I am trying to access my server via ssh from my laptop. both have ubuntu. the server is 9.10 desktop, and the laptop is 9.04 desktop.

here is my error.

```

nathan@lappy:~/.ssh$ chmod 600 ~/.ssh/authorized_keys
nathan@lappy:~/.ssh$ ssh 192.168.1.105
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for '/home/nathan/.ssh/id_rsa' are too open.
It is recommended that your private key files are NOT accessible by others.
This private key will be ignored.
bad permissions: ignore key: /home/nathan/.ssh/id_rsa
Permission denied (publickey).

```


to generate the key I used the following on my server box:
```

ssh-keygen -f ~/.ssh/id_rsa -t rsa -b 4096
cat id_rsa.pub >> authorized_keys
[code]

Then I sshed into my server using a password to access the id_rsa file. I used a text editor to copy the id_rsa file from my server to my laptop.
I have gone through and ran these commands
[code]
chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_key

```

Something is clearly wrong here, but I am missing it.

Can someone please help me get back on track?

---

### Post by synapsys on 2009-12-21
You want to generate the key on your **local** machine, then transfer it to your **remote** machines authorized_keys file. See link for details....

[http://news.softpedia.com/news/How-to-Use-RSA-Key-for-SSH-Authentication-38599.shtml](http://news.softpedia.com/news/How-to-Use-RSA-Key-for-SSH-Authentication-38599.shtml)

---

### Post by Neezer on 2009-12-21
> **synapsys said:**
> You want to generate the key on your **local** machine, then transfer it to your **remote** machines authorized_keys file. See link for details....

[http://news.softpedia.com/news/How-to-Use-RSA-Key-for-SSH-Authentication-38599.shtml](http://news.softpedia.com/news/How-to-Use-RSA-Key-for-SSH-Authentication-38599.shtml)


in your explaination does local = my laptop and remote = server?

I want to log into the server from my laptop....

---

### Post by bodhi.zazen on 2009-12-21
On your client (not server)

```
chmod 400 /home/nathan/.ssh/id_rsa
```

---

### Post by synapsys on 2009-12-21
> **Neezer said:**
> in your explaination does local = my laptop and remote = server?

I want to log into the server from my laptop....

Yes.

You can repeat this process for any and all machines you want to use to ssh into your server. You generate the key on your local machine and then add it to the set of authorized keys on your server.

---

### Post by Neezer on 2009-12-21
ok...I'm trying to follow this guide
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Generating%20RSA%20Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Generating%20RSA%20Keys)

Success!!!

I just had to generate the keys on my laptop (the client) and then send the key over to the server (the host).

typos never help either...

now it is a matter of port forwarding on my router to be able to access it from outside of my network. shouldn't be too tough as i've done this before.

Thanks for the help. I really appreciate it!

---

### Post by synapsys on 2009-12-21
Glad you got it working. You might also want to consider changing the default port from 22 to something else for extra added security.

---

