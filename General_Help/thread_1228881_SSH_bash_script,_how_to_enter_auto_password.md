---
title: "SSH bash script, how to enter auto password?"
date: 2009-08-01
forum: General Help
---

### Post by Screatch on 2009-08-01
I want everytime i launch a bash script to connect to a ssh server.
Unfortunately for me, server have a very hard password and typing it manualyl everytime is a problem.
Is there anyway i can tell the bash script what the server password is so i won't have to type it? If yes, how?

Dont offer me public keys authenication as there are some problems that does not allow me to do this.

---

### Post by slakkie on 2009-08-01
(I would do it with keys...)

---

### Post by Screatch on 2009-08-01
I would too but unfortunately when i am importing key to server i get an error
stdin: is not a tty.
Running centos on server.

---

### Post by slakkie on 2009-08-01
> **Screatch said:**
> I would too but unfortunately when i am importing key to server i get an error
stdin: is not a tty.
Running centos on server.

ssh-copy-id [email]uid@server.name.com[/email] 

should do the trick..

---

### Post by Screatch on 2009-08-01
Nevermind, found the solution installing the sshpass and using command something like this.

sshpass -p 'heregoespassword' ssh [email]user@server.com[/email]

---

### Post by HermanAB on 2009-08-01
Fantastic!  I was unaware of sshpass.  Together with parallel ssh (pssh), this may sometimes be extremely handy.

---

