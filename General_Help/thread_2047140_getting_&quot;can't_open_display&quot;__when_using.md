---
title: "getting &quot;can't open display&quot;  when using ssh"
date: 2012-08-24
forum: General Help
---

### Post by marinara on 2012-08-24
I'm used to ssh-ing to my other box, and running GUI apps after setting DISPLAY=:0  
The X server is on the box i'm ssh-ing to because i'm not using ssh -X.
With the upgrade to 12.04.1, this stopped working (coincidence?)

I'd like to get this working so I can run programs from ssh.

---

### Post by sanderj on 2012-08-24
> **marinara said:**
> I'm used to ssh-ing to my other box, and running GUI apps after setting DISPLAY=:0  
The X server is on the box i'm ssh-ing to because i'm not using ssh -X.
With the upgrade to 12.04.1, this stopped working (coincidence?)

I'd like to get this working so I can run programs from ssh.

FWIW: The X *server* is the computer having a physical display, so normally the computer in front of you.

DISPLAY=:0 ... ? That points to the same machine. No IP address needed?

And why don't you use 'ssh -X'? That works for me without difficult DISPLAY stuff.

---

### Post by dozdozez on 2012-08-24
May be a question of permissions. Type:
```
xhost
```

This command will tell you which users has access to that computer's X server. 
If your user is not listed, add it:
```
xhost +SI:localuser:<user>
```

If you want to grant access to anyone you can do so with  xhost +, but this is not recomended for security iissues.

I hope this work for you.

---

### Post by Lars Noodén on 2012-08-24
To followup on what  sanderj wrote, you need to have the x-server on the machine on which you will actually do the viewing.  Then connect to the remote machine with the -X option.  Setting DISPLAY=:0 on the remote machine will cause the program to be displayed on the remote machine itself, if it has an X-server running.  

Alternately, instead of using the -X option each time, if you're always going to use X forwarding, you could modify ~/.ssh/config and make an entry for that host:

```

Host otherbox
  HostName otherbox.example.edu
  ForwardX11 yes

```

Either way, you want to leave the DISPLAY variable alone.

---

### Post by Rexilion on 2012-08-24
For me, sometimes

> ssh -Y

works. (and no, this is not a lame joke ;))

---

### Post by marinara on 2012-08-24
I tried xhost + 
Didn't work.
ssh -X works fine. That's not my problem.  I want the X server to be on the machine I ssh to.  Most likely I installed something stupid, and broke it somehow.

---

### Post by marinara on 2012-08-24
[http://ubuntuforums.org/showpost.php?p=10284244&postcount=11](http://ubuntuforums.org/showpost.php?p=10284244&postcount=11)

oops, apparently I was doing 
DISPLAY=:0
when i needed to do 
export DISPLAY=:0

:(

marking thread as solved.  thanks for pushing the ball foward.  I feel much relieved.

---

