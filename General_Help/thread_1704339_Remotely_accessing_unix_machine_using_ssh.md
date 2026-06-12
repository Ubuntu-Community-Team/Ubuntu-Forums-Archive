---
title: "Remotely accessing unix machine using ssh"
date: 2011-03-10
forum: General Help
---

### Post by jboi on 2011-03-10
I am trying to set up a ssh server on my desktop computer. It runs Ubuntu 10.04 with Win 7 (dual boot). I want to ssh into my desktop from any other machine (from anywhere), and I'm not sure if setting up a ssh server is the right thing to do. Also, is it secure? what kind of encryption does it use?

Any help would be great! 

-jboi

---

### Post by Kirboosy on 2011-03-10
Hi JBoi! Welcome to the Forums! :)

[Official SSH Ubuntu Documentation]("https://help.ubuntu.com/community/SSH")

SSH is secure when properly configured. :)


~Caboose

---

### Post by jboi on 2011-03-10
Great! Thanks :D

---

### Post by WinterMadness on 2011-03-10
all you really need is to setup the ssh server, and port forward port 22 TO your server and youre good to go.

Granted, youll want to setup some security.

---

### Post by Kirboosy on 2011-03-10
I actually would forward 2 ports to the server. Port 22 and the other port should be a random unused port.

Some public places automatically block port 22 because they know its SSH. If you use a random port and they don't block the SSH protocol you will still be good to go. :)


~Caboose

---

### Post by lithopsian on 2011-03-10
You ask if ssh is secure?  It can be but what you are intending has risks.  The only real secure way to use ssh is to setup keys for authentication.  Using a username and password is subject to brute force dictionary attacks, so you'd better make sure that you have a really complex password.

If you know the machines you will want to connect from then you can exchange keys and turn off password authentication.  You can even restrict the IP addresses that are allowed to connect.  Another trivial trick is to switch off port 22 and use a different port, which will reduce the number of attacks on your machine (there *will* be attacks if you use port 22, and probably eventually any other port also).

Switch off root access to ssh, to make it difficult for anyone who does break in to do damage.  Of course if they broke in by using your password then they can still sudo things, so think about whether the user you ssh with should have any sudo access.

---

