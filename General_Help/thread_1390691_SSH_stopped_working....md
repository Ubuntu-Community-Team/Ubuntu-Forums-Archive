---
title: "SSH stopped working..."
date: 2010-01-25
forum: General Help
---

### Post by IamAbanana on 2010-01-25
I just started using Ubuntu (9.10) a week or so ago.  I was using the terminal to connect to our school computer to compile my project (I was writing it on my home pc).  I installed Ubuntu (9.10) on my wife's computer no more than 1 hour ago.  Immediately after I installed it (Ubuntu), I could no longer SSH into my school (ssh1.cs.uwf.edu).  I don't know if it stopped being able to connect because of her install (I know I probably sound stupid for even bringing this up), and I have no idea how to troubleshoot with this OS.  I would greatly appreciate any help you guys/girls could offer.

The only thing I came across was somebody telling others to write stuff in the terminal like:
```
ssh localhost
ssh: connect to host localhost port 22: Connection refused

ssh: 0.0.0.0/0.0.0.0
No command 'ssh:' found, did you mean:
 Command 'ssh' from package 'openssh-client' (main)
 Command 'sshm' from package 'sshm' (universe)
 Command 'sshd' from package 'openssh-server' (main)
ssh:: command not found

```Anything else I can do to let you know what problems I'm having?

I hope you don't mind me asking, thanks for any help :)

I just found out, it does not work on hers either.

---

### Post by llamabr on 2010-01-25
try:

```
sudo apt-get install ssh
```

Though I doubt that's the problem.  If not, post the actual output of your error

---

### Post by IamAbanana on 2010-01-25
I just found out it's not working on hers either.  I just tried that and it did not help.  After I try connecting, it just sits there.  I saw a timeout message once, but that was it.

What do you mean the output of my error?  If you mean "what it says when it won't connect".  

The last 2 time I've gotten 
```
ssh: connect to host ssh1.cs.uwf.edu port 22: Connection timed out
```

---

### Post by llamabr on 2010-01-25
ya, there's something wrong with that server, I think.  What I mean is type:

```
ssh -v username@ssh1.cs.uwf.edu
```

and then copy the output.  i think the server is down right now.  Give them a call and see.

---

### Post by IamAbanana on 2010-01-25
> **llamabr said:**
> ya, there's something wrong with that server, I think.

Yeah...you're right.  Thanks anyways :D

---

