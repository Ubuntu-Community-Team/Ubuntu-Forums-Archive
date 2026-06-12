---
title: "Renaming the smb.conf file"
date: 2011-04-05
forum: General Help
---

### Post by rsnow on 2011-04-05
I am trying to follow the instructions in the smb.conf file  which says, "name original file smb.conf.master and create the "real" config file with test parm -s smb.conf.master >smb.conf".

First I made myself the owner of the smb.conf file. Then I tried to rename the smb.conf file to smb.conf.master. When I try to do this with: 
	
	rename smb.conf smb.conf.master
the result is: 
Bareword "smb" not allowed while "strict subs" in use at (eval 1) line 1.
Bareword "conf" not allowed while "strict subs" in use at (eval 1) line 1.

Can someone tell me what this means, (why it is happening) and what do I need to do in order to rename the smb.conf file to smb.conf.master.

---

### Post by i.r.id10t on 2011-04-05
the rename command is actually perl related, and not the rename command you think it is.

Use 

```

mv smb.conf smb.conf.master

```

Use mv - and move it to a new name

---

### Post by rsnow on 2011-04-05
Hey thanks! That worked insofar as I was able to rename the file. Now my problem is that I am being denied making a copy named smb.conf

I first tried using test parm -s smb.conf.master >smb.conf
result was bash: smb.conf: Permission denied

I then tried sudo test parm -s smb.conf.master >smb.comf
result was the same

It is really discouraging when I follow the instructions given in the file and they do not work. I guess those instructions were written for a different version of Linux?

---

### Post by Toafan on 2011-04-05
Well, I can tell you how to copy the actual file...

To copy from the command line, use the cp command, like so:
```
cp smb.conf.master smb.conf
```This will copy the smb.conf.master file you 'made' earlier to smb.conf.
(I actually didn't know that until I looked it up on a hunch)

Based on a quick glance at some of the various samba man pages, it seems testparm looks for the file smb.conf - which, if you don't have, will result in failure.
I'd say you should EITHER do:
```
man testparm
```and read the man page, OR, after copying and editing the config file:
```
testparm -s
```There MAY be an option to specify what file to test as the config file, but I havn't tried to see if it is (see man testparm).


I wonder if there's a "new-user's guide to basic command line usage" out there. I don't know of any good ones. I think I'll slap one together and put it in my sig :)

---

### Post by rsnow on 2011-04-05
That looks sensible. I'll give it a try in a little while. Gotta tend to some other matters first. I'll post back with my results. Your idea about an updated guide sounds good.Thanks for your help.

---

### Post by Toafan on 2011-04-05
If You're still reading this, also check out [linuxcommand.org]("http://linuxcommand.org/") (I added it to my sig, but my sig didn't get added to my previous post). The guy who wrote it steps through learning all about how to effectively use the command line. Actually, it might even be the basic guide I was talking about.

---

### Post by rsnow on 2011-04-06
It worked. Bu using sudo cp smb.conf.master smb.conf, I made the copy and then tested it with testparm -s. It tested OK. Many thanks for the help.

---

