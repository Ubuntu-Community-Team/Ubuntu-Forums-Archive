---
title: "ssh explanation"
date: 2010-05-31
forum: General Help
---

### Post by SquidLord on 2010-05-31
Maybe I'm doing something wrong, but I have a slight issue with SSH between my iPhone and my computer.

so I do the command:
```
scp root@[iPhone's IP]:/path/to/file SquidLord@[computer's IP]
```
and it puts the file [which is a text file btw] in my in my user name folder [ie: /home/SquidLord] named "SquidLord@[computer's IP]"

following what I believe to be the correct syntax to place the file where I want it gives me the error "Host key verification failed"
The syntax I believe to be correct is:
```
scp root@[iPhone's IP]:/path/to/file SquidLord@[computer's IP]:/home/SquidLord/Documents/
```

What exactly am I doing wrong?

---

### Post by yeats on 2010-05-31
Okay, a couple of things... first of all, you should be able to form your command like this, without the "root@":

```
scp /path/to/file SquidLord@[computer's IP]:/home/SquidLord/Documents/

```

You can just name the file.  However...

> it gives me the error "Host key verification failed"

means that your iphone has a different host key in ~/.ssh/known_hosts for your PC than your PC actually has (did you reinstall recently?).  The solution is to delete the offending line in ~/.ssh/known_hosts.  The text of the error should tell you the line number.

---

### Post by Dejavou42 on 2010-05-31
Just out of curiosity, why not use iphone ftp app from Rock or Cydia? I'm using vsftpd and it works great. You will need to take a look at this forum to get it working properly though... [http://www.ipodtouchfans.com/forums/showthread.php?t=107342](http://www.ipodtouchfans.com/forums/showthread.php?t=107342). Hope this helps.

---

### Post by SquidLord on 2010-06-01
> **chrissharp123 said:**
> Okay, a couple of things... first of all, you should be able to form your command like this, without the "root@":

```
scp /path/to/file SquidLord@[computer's IP]:/home/SquidLord/Documents/

```

You can just name the file.  However...



means that your iphone has a different host key in ~/.ssh/known_hosts for your PC than your PC actually has (did you reinstall recently?).  The solution is to delete the offending line in ~/.ssh/known_hosts.  The text of the error should tell you the line number.

Well, I used to be able to just do it with the command in my OP. but after logging into my iPhone and doing your command it registered my computers key and allowed the transfer to go where I aimed it keeping the name and all. To answer your question though, yes I did reinstall recently.

Now I get something different when performing my original command.
```
root@[iPhone's IP]'s password: 
Permission denied, please try again.
Permission denied, please try again.
Permission denied (publickey,password).
lost connection

```

On the plus side, I AM able to copy files after logging into the actual device \\:D/





> **Dejavou42 said:**
> Just out of curiosity, why not use iphone ftp app from Rock or Cydia? I'm using vsftpd and it works great. You will need to take a look at this forum to get it working properly though... [http://www.ipodtouchfans.com/forums/showthread.php?t=107342](http://www.ipodtouchfans.com/forums/showthread.php?t=107342). Hope this helps.

Well, this requires less setup and I prefer to familiarize myself with Terminal; as I'm new-ish to Ubuntu [I've used it before, but only with basic functions].

---

