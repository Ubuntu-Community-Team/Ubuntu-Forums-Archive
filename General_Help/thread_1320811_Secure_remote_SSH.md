---
title: "Secure remote SSH?"
date: 2009-11-09
forum: General Help
---

### Post by knottshawk on 2009-11-09
I've seen dozens of discussions on variations of this topic, but they don't answer my specific questions. I want to remotely access my Ubuntu 8.10 box which is behind a router. I'm sure I can lookup the "how to" of enabling ports on my router and Ubuntu box (I already run open SSH server) but what I want to know is:
- How secure is it to open a port, any port, on my router? Am I opening myself up to bruteforce attacks? (it should be noted that I have Windows machines behind the same router) 
- How secure is SSH? Is it, in itself, vulnerable to bruteforce attacks?

I plan to use an obscure port, not port 22, but am still wondering how to insure security? Anything else I should consider?

---

### Post by alphaniner on 2009-11-09
[Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812")
[Ubuntu Wiki configure SSH]("https://help.ubuntu.com/community/SSH/OpenSSH/Configuring")
[Ubuntu wiki SSH Keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys")

I'm not a security guru, but my understanding is that you want to use port forwarding on your router, and use keys rather than password for authentication.

---

### Post by bchurchill on 2009-11-09
> **knottshawk said:**
> 
- How secure is it to open a port, any port, on my router? Am I opening myself up to bruteforce attacks? (it should be noted that I have Windows machines behind the same router) 
- How secure is SSH? Is it, in itself, vulnerable to bruteforce attacks?


A port is as secure as the application listening to it.  What you want to do is forward a port on your router to the ssh port on your Ubuntu box, and unless you want more services, make this the only forwarded port.  In that case, it's not really an issue for windows computers to be on your network since no ports are being forwarded to the windows computers. 

This begs the question, of course, how secure ssh is.  It's rather secure.  All data transfered (including your password) is encrypted.  It is possible to brute force it, but this shouldn't be a worry if you choose a strong password (long with uppercase, lowercase, numbers and symbols).  

> **knottshawk said:**
> 
I plan to use an obscure port, not port 22, but am still wondering how to insure security? Anything else I should consider?


If you know what computer(s) that will be accessing your Ubuntu box remotely you can restrict access to them by IP-address.  Between this and using an obscure port, chances are nobody, or very few people, are going to find your server in the first place.

To be certain that nobody is executing a man-in-the-middle attack, it's a good idea to write down your computer's RSA key fingerprint and take it with you.  When you ssh into your computer for the first time you'll see a message like:

"The authenticity of host 'mycomputer.mydomain.com (111.111.111.111)' can't be established.
RSA key fingerprint is 90:ab:6a:31:0b:81:62:25:9b:11:50:05:18:d3:1a:b5.
Are you sure you want to continue connecting (yes/no)?"

If the key matches what's on your paper, you're in good shape.  The client will save the RSA fingerprint and check it automatically next time you login.


Hope that helps!  Ask if you have more questions.  There's all sorts of information out there about securing your ssh server, just google away.

---

### Post by shaggy999 on 2009-11-09
You might also want to look into installing a port knocker. It's like having a "secret handshake" that only you and the computer know so that it knows you are allowed to communicate on a particular port, otherwise it ignores traffic.

---

### Post by knottshawk on 2009-11-09
Good info...thanks! ):P

---

