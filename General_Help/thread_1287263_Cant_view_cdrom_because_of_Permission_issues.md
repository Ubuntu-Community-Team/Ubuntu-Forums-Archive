---
title: "Cant view cdrom because of Permission issues"
date: 2009-10-09
forum: General Help
---

### Post by dracule on 2009-10-09
I can't view /media/cdrom as a normal user. if I cd into as a super user, i can view it. If i launch a nautilus window as a super user, I can view it. 

As a normal user it is empty. If i try to access it from "computer://" then i get a "cannot mount file"

The cd is a data DVD I burnt on Windows Vista last year. It reads fine on a Windows machine, and I can view the files as a super user, but I cant do anything with the files. 

I tried to copy them to the desktop and got a "you do not have permission". I cannot change the permissions through the "properties" window because it is "read only" (according to the error).

Help?

---

### Post by Boondoklife on 2009-10-09
Are you sure your user is part of the cdrom group?

---

### Post by dracule on 2009-10-10
the box is checked "use CD-ROM Drives" I am pretty sure Vista put some file permissions on it and all my other data files. I can use other cd's made with Ubuntu just fine, but the ones made with vista, have permissions troubles.

---

### Post by dracule on 2009-10-10
bump

---

### Post by delcypher on 2009-10-10
In terminal (Applications > Accessories > Terminal) run:
> id

This will list what groups you are a member of. You need to a member of cdrom.

If you are not a member then run (where username is your username)
> sudo gpasswd -a username cdrom

Let us know how you get on.

---

### Post by dracule on 2009-10-10
> **delcypher said:**
> In terminal (Applications > Accessories > Terminal) run:


This will list what groups you are a member of. You need to a member of cdrom.

If you are not a member then run (where username is your username)


Let us know how you get on.

I told you already... I AM A MEMBER OF CDROM

```
phun@desktop:~$ id
uid=1000(phun) gid=1000(phun) groups=4(adm),20(dialout),24(cdrom),46(plugdev),109(lpadmin),117(admin),122(sambashare),1000(phun)

``` 

gosh, Ubuntu forums have really gone down hill. Every problem I have I repeat myself several times over the course of several days and the problem never gets resolved.

before you would ask a question and immediately somebody would actually read your post and  give you an intelligent answer. That was the reason for choosing ubuntu.

---

### Post by dhughes on 2009-10-10
Good bye, good luck.

---

### Post by dracule on 2009-10-10
> **dhughes said:**
> Good bye, good luck.

You dont understand, this is the FOURTH problem in the past two weeks where I say something "I did [insert X]", 12 hours later somebody asks "did you do [insert X]" I say "yes" very politely, another 12 hours pass and then another person comes along and says "did you [insert X]" I say yes again very politely, 24 hours pass I bump the thread and then somebody asks "did you [insert X]"


I have no idea how the forums got like this, but none of my problems have been fixed.

---

### Post by delcypher on 2009-10-10
> **dracule said:**
> I told you already... I AM A MEMBER OF CDROM

```
phun@desktop:~$ id
uid=1000(phun) gid=1000(phun) groups=4(adm),20(dialout),24(cdrom),46(plugdev),109(lpadmin),117(admin),122(sambashare),1000(phun)

``` 

gosh, Ubuntu forums have really gone down hill. Every problem I have I repeat myself several times over the course of several days and the problem never gets resolved.

before you would ask a question and immediately somebody would actually read your post and  give you an intelligent answer. That was the reason for choosing ubuntu.

Correction you never said you were a member of the CDROM group, you said "use CD-ROM Drives". Which probably means the same thing but I'm not 100% sure.

> intelligent answer
Fix it yourself.

Did have a bunch of other suggestions to fix your problem but screw it, you want to be an ***-hole then fine.

---

### Post by Boondoklife on 2009-10-10
Ok guys lets pull ourselves out of the mud throwing contest and leave that to the politicians.

try to put the cd in and in a terminal do:
```
cd /media
ls -la[

cd /media/cdrom
ls -la/CODE]

and see what it gives you for rights listing. Once we have this, we can look into the righs bit.

If you can read the cd via gksudo nautilus then you could copy the files to a folder on the desktop then in a shell change the permissions.
[CODE]cd ~/Desktop
chown USERNAME:USERNAME * -fR
chmod 755 * -fR
```

That should atleast get you the files till you figure out what you cant see them as a normal user.

---

### Post by mick55 on 2009-10-10
Excuse me, but does anyone here have a job?
Or go to school?
Or raise a family?
Or have a life?

Or do you all just live off the big money you
get paid for answering questions for fellow
Linux users?

Oh sorry, i forgot, you don't get paid for this
free tech support do you.

Wow, you don't even get paid for all the abuse heaped on you
for not having exact answers for vague questions.

You should quit this lousy job.

Oh wait, you can't, because i'ts not a job,
i'ts just some nice guys using their valuable time to help
others in the community that haven't quite got there yet.

I want to shout too.:P

HAVE A NICE DAY!!!!!

---

