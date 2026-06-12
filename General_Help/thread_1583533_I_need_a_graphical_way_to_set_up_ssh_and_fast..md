---
title: "I need a graphical way to set up ssh and fast."
date: 2010-09-28
forum: General Help
---

### Post by darkstarbyte on 2010-09-28
My older brother is switching to Linux and I wanted to set up ssh with him but a graphical but because he is new he needs a graphical way. I was going to download updates and everything he needs from here but I need a way so he can set up ssh and I can do the command line stuff. 

He wants to use Linux because of wine, ktorrent, xchat, the virus thing, and because of the gui package manager.

---

### Post by sendblink23 on 2010-09-28
> **darkstarbyte said:**
> My older brother is switching to Linux and I wanted to set up ssh with him but a graphical but because he is new he needs a graphical way. I was going to download updates and everything he needs from here but I need a way so he can set up ssh and I can do the command line stuff. 

He wants to use Linux because of wine, ktorrent, xchat, the virus thing, and because of the gui package manager.

hmm I think Filezilla does ssh
[http://filezilla-project.org/](http://filezilla-project.org/)

---

### Post by darkstarbyte on 2010-09-28
> **sendblink23 said:**
> hmm I think Filezilla does ssh
[http://filezilla-project.org/](http://filezilla-project.org/)


Filezilla is a file transfer protocol program.

---

### Post by willskills on 2010-09-28
Applications > Ubuntu Software Centre

Search for openssh?

---

### Post by envygeeks on 2010-09-28
```

sudo aptitude install openssh-server --without-recommends

```

Shouldn't be too hard for him to do since it is after all a one line win command :P

---

### Post by luvshines on 2010-09-28
If I got it right, what you need is to just access his desktop so that you can do all the command line stuff for him.

That can be done by "remote desktop" or setting up SSH server with Xforwarding on ur brother's system and then connecting it.

Or do you want that his system gets to download updates and configuration stuff from your PC ?

---

### Post by linux-hack on 2010-09-28
well why not try remote desktop ? or vnc with ssh  ?

---

### Post by sendblink23 on 2010-09-28
> **darkstarbyte said:**
> Filezilla is a file transfer protocol program.

I've used FIlezilla to SSH into my iphone many times...

since I did ssh on it that is why I mentioned it

---

### Post by linux-hack on 2010-09-28
> **sendblink23 said:**
> I've used FIlezilla to SSH into my iphone many times...

since I did ssh on it that is why I mentioned it

Yes you can connect to a machine with it but you'll not be able to lunch commands. When you connect with filezilla on ssh acutaly you connect through sftp. Correct me if I'm wrong.

---

### Post by robsoles on 2010-09-28
> **willskills said:**
> Applications > Ubuntu Software Centre

Search for openssh?

openssh-server

that is the package you want to install, whether in synaptic, software center or from command line is your call.

---

