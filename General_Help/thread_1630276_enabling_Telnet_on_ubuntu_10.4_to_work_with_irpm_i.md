---
title: "enabling Telnet on ubuntu 10.4 to work with irpm iphone app"
date: 2010-11-24
forum: General Help
---

### Post by Viper2011 on 2010-11-24
I believe telnet is installed on my desktop but when i go into the file system to find the xinetd/telnet file to edit it i cant find it. I am wanting to setup telnet to work with the iphone app IRPM to remotely shut down my pc. Any ideas?

---

### Post by dcstar on 2010-11-24
> **Viper2011 said:**
> I believe telnet is installed on my desktop but when i go into the file system to find the xinetd/telnet file to edit it i cant find it. I am wanting to setup telnet to work with the iphone app IRPM to remotely shut down my pc. Any ideas?

The telnet client is installed by default, the telnet server is not.

---

### Post by Viper2011 on 2010-11-25
It seems if i already installed the telnet server. To setup irpm to work o ubuntu and telnet i need to find the xinetd/telnet file and edit the disable yes line in it. The trouble is i cant find it in the file system. I have tried the sudo restart commands but nothing happens in the terminal.

---

### Post by sanderj on 2010-11-25
Why are you trying to use telnet? It's unsafe. Use ssh instead.

---

### Post by Viper2011 on 2010-11-25
I am trying to use a iphone app called irpm to remotely shutdown my computer from outside my network.Irpm only uses telnet to do that.

---

### Post by t4thfavor on 2010-11-25
Don't do it, telnet is really easily sniffed, and I would bet that your not going to want someone to have a sudo enabled account accessable from the internet.

If you have to do it, create a user who has a really good password that isn't a password you normally use, and only has the ability to shutdown the PC.

---

### Post by CharlesA on 2010-11-25
Doesn't the iphone have an SSH client for it?

It's [here]("http://webdesign.about.com/od/iphoneapps/tp/iphone_ssh_tools.htm").

---

### Post by t4thfavor on 2010-11-25
Yeah, but it looks like the app he is setting up only uses telnet, which really stinks.

---

### Post by CharlesA on 2010-11-25
> **t4thfavor said:**
> Yeah, but it looks like the app he is setting up only uses telnet, which really stinks.

Indeed.

If all the OP wants to do is shut down the PC remotely, he can use an SSH client to connect and run *sudo halt*. *shrugs*

---

### Post by t4thfavor on 2010-11-25
Then why did he spend 300$ on an iphone :)  I thought that answer was too obvious...

I don't know, but maybe this is an automated iphone app that only supports telnet over token ring, with the Apple iToken token ring adapter (sold seperatly).

*Also Shrugs*

---

### Post by CharlesA on 2010-11-25
There are SSH clients for Android and other smartphones, I'm sure.

There's no way in hell you'd catch me using telnet unless I'm doing something like flashing my router.

---

### Post by Viper2011 on 2010-11-25
Thanks for the info. Its not a big deal, just something i was playing around with. Great forum.

---

