---
title: "How can I set up a secure home server?"
date: 2011-01-13
forum: General Help
---

### Post by smdawson on 2011-01-13
I have been doing a whole lot of reading on any kind of home server. I want to have a secure home server that I can access from school by a domain name. At first I was looking at FTP, but I need something secure and it seemed like the software that supported SFTP has to be purchased. Then I started looking at SSH stuff, but I also realized that I want to use a dynamic DNS, so I started reading about that. 

Basically, now my head is so information-logged I can't figure out what and how I should do this. If anyone could give me some very step-by-step-procedure links (or information) that show me how to set up a secure home server that I can access with a domain name through the internet that also uses a DDNS, that would solve all my problems.

---

### Post by 3Miro on 2011-01-13
Get a router that supports DDNS like [https://www.dyndns.com/](https://www.dyndns.com/), they have step by step instructions on how to set things up (together with port forwarding, which depends on the router). This is the easiest way to fix that issue. If you don't get a router, you will need to get their software installed, read their instructions.

Then you can setup ssh, check the official Ubuntu HowTo is very easy to follow. If it is just for you, ssh will do both admin tasks and ftp tasks. If you want to have ti available to other people, you can then move into FTP.

Basically, take it one step at a time.

---

### Post by cptrohn on 2011-01-13
Is the machine going to be a dedicated server?  If so couldn't you just use ubuntu server edition?  Or maybe use Ubuntu server edition and then add the ubuntu desktop to it?

---

### Post by tredegar on 2011-01-13
Setting all this up is slightly complicated, but interesting, great fun if you enjoy an intellectual challenge, and you are about to learn a lot of useful stuff. 

But if you are going to open **ssh** to the big bad internet, first make sure you are going to be secure. 

The most important thing you need to do is _enable_ public / private key-based authentication (this will also mean that you will not even have to provide a password when you login, because authentication will be handled securely) and then _disable password authentication_ (see **man ssh_config** and scroll down to  **PasswordAuthentication** )

Here's a link to a [HOWTO]("http://www.linuxquestions.org/linux/answers/Networking/Public_key_authentication_with_ssh")

Once you have **ssh** set up, sftp://user@hostname is easy (even in nautilus !)

The way **ssh** is set up is that it will _not_ work if it is badly configured. This seems to be intentional, because there'd be no point in a "secure" shell running if it detected insecurities in configuration. This can be frustrating at first, but as you read and learn, you'll eventually understand.

It would be a good idea to practice this (connecting PCs with **ssh**) on your LAN *before* you open or forward any ports on your router's firewall. 

If you do not have linux at school, then life might be a little more complicated, because as I understand it (I don't run win) windows is not "out of the box", as flexible or configurable with networking as linux is.

Anyway, have fun.
Best wishes.

---

### Post by tredegar on 2011-01-13
Setting all this up is slightly complicated, but interesting, great fun if you enjoy an intellectual challenge, and you are about to learn a lot of useful stuff. 

But if you are going to open **ssh** to the big bad internet, first make sure you are going to be secure. 

The most important thing you need to do is _enable_ public / private key-based authentication (this will also mean that you will not even have to provide a password when you login, because authentication will be handled securely) and then _disable password authentication_ (see **man ssh_config** and scroll down to  **PasswordAuthentication** )

Here's a link to a [HOWTO]("http://www.linuxquestions.org/linux/answers/Networking/Public_key_authentication_with_ssh")

Once you have **ssh** set up, sftp://user@hostname is easy (even in nautilus !)

The way **ssh** is set up is that it will _not_ work if it is badly configured. This seems to be intentional, because there'd be no point in a "secure" shell running if it detected insecurities in configuration. This can be frustrating at first, but as you read and learn, you'll eventually understand.

It would be a good idea to practice this (connecting PCs with **ssh**) on your LAN *before* you open or forward any ports on your router's firewall. 

If you do not have linux at school, then life might be a little more complicated, because as I understand it (I don't run win) windows is not "out of the box", as flexible or configurable with networking as linux is.

Anyway, have fun.
Best wishes.

---

### Post by smdawson on 2011-01-13
Ok, my router does support DDNS. 

I checked out DynDNS.com as well. Am I using the IP address that DynDNS.com tells me I am at right now, or is the IP address for my router different?

I am still a little confused about SSH. I downloaded OpenSSH but have not created a public key.The [link]("http://www.linuxquestions.org/linux/answers/Networking/Public_key_authentication_with_ssh") says I need to enter a strong 10-30 character passphrase, but then it also says I should just not enter a passphrase, but this will be less secure. So what do I do?

My final question is how will SSH and DynDNS come together? Don't I have to link them or my directories to something...and will all of this be secure?

---

### Post by CharlesA on 2011-01-13
If someone gets a hold of your private key and it doesn't have a passphrase, they would have access to your server without having to know your password.

You set up DynDNS to point to your ip address and then forward port 22 on your router.

DynDNS is only there in case your ip address changes.

---

### Post by smdawson on 2011-01-13
Ok, I set up an example.dnydns.org hostname. I have the ddns successfully updated on my router, but I am not sure that I have done the port forwarding correctly.

Assuming that I have done this right, what is my next step?

---

### Post by CharlesA on 2011-01-13
Check [http://www.canyouseeme.org/](http://www.canyouseeme.org/) to see if the port is open to the internet.

---

### Post by smdawson on 2011-01-13
Yes. The port is good. I have also set up the passphrase for the public key. What now?

---

### Post by CharlesA on 2011-01-13
Should be fine now. Just be sure to disable password logins in sshd_config.

---

### Post by smdawson on 2011-01-14
Actually, I am having problems with the pubkey authentication. I am still getting asked for a password. According to the "[troubleshooting help]("http://www.linuxquestions.org/linux/answers/Networking/Public_key_authentication_with_ssh")" section I am getting the correct feedback and have the right setup.

---

### Post by tredegar on 2011-01-14
Check your permissions
**~/.ssh** needs to be 700
**~/.ssh/id_rsa** needs to be 600
**~/.ssh/id_rsa.pub** needs to be 644

But if you have set up a passphrase for the public key, you will still be asked for that.

---

