---
title: "Beginner Question on root"
date: 2011-05-14
forum: General Help
---

### Post by ghosticmp19 on 2011-05-14
I tried to post in absolute beginner talk but it wouldn't let me. After reading part of a book for an intro class in Linux I came across directories. They all pretty much make sense but what exactly is in the /root directory in ubuntu? The book just says "Home directory for root". And why can't I access it through cd /root. It says permission denied. I tried also sudo cd /root and it gave me an error. I googled it and just got worthless information on changing root passwords.

---

### Post by Flugz on 2011-05-14
Just like you have a home directory under /home/<username>/, where you can save your files and customize your environment. The superuser (root) will save his files and changes made to his environment in the /root directory.

So, basically, /root is where the system administrator would hide his porn, inaccessible and out of sight for normal users.

---

### Post by ghosticmp19 on 2011-05-14
Oh ahaha ya I guess I assumed because I could use "sudo" and I'm the only user on my computer that I was the administrator. Apparently not? I guess that's why I'm getting permission denied. I guess I will follow those tutorials on becoming a root user and explore with "ls" the contents of the directory. Hopefully that will work.

---

### Post by Flugz on 2011-05-14
You are the administrator ;)

Do this:
```
sudo su
```then:
```
whoami
```and just type exit to stop being root.

---

### Post by ghosticmp19 on 2011-05-14
Doh! Thanks ! It let me in now :).

---

### Post by PsyclonJohn on 2011-05-14
To get into the root file system you can run

```
gksudo nautilus
```

---

### Post by shashanksingh on 2011-05-14
> **ghosticmp19 said:**
> I tried to post in absolute beginner talk but it wouldn't let me. After reading part of a book for an intro class in Linux I came across directories. They all pretty much make sense but what exactly is in the /root directory in ubuntu? The book just says "Home directory for root". And why can't I access it through cd /root. It says permission denied. I tried also sudo cd /root and it gave me an error. I googled it and just got worthless information on changing root passwords.

there is no such thing as sudo cd
cd is not a program , its a bash command.
you can be sudo to run programs in that mode.

sudo su

and then cd /root

---

### Post by jerome1232 on 2011-05-14
> **shashanksingh said:**
> 
cd is not a program , its a bash command.


That is an interesting tidbit to me, I had always assumed all "commands" were actually just programs. But I guess bash is an interpreted programming(maybe scripting is a better word) language is it not? So it does make sense that some things are just bash commands.

Anyways that was interesting to me :D

---

### Post by Flugz on 2011-05-14
> **jerome1232 said:**
> That is an interesting tidbit to me, I had always assumed all "commands" were actually just programs. But I guess bash is an interpreted programming(maybe scripting is a better word) language is it not? So it does make sense that some things are just bash commands.
Thought that was a bit interesting myself. I know bash have quite a few built in commands, but out of curiosity I had to open a shell and verify it for myself. 
```
which history hash cd eval
~$
``````
which date w firefox users
/bin/date
/usr/bin/w
/usr/bin/firefox
/usr/bin/users
~$
```Just took in something very basic :cool:

---

### Post by shashanksingh on 2011-05-14
> **jerome1232 said:**
> That is an interesting tidbit to me, I had always assumed all "commands" were actually just programs. But I guess bash is an interpreted programming(maybe scripting is a better word) language is it not? So it does make sense that some things are just bash commands.

Anyways that was interesting to me :D
Yeah even I had that misconception. Then I realised cd is just like if and else, a "keyword" for bash, while cp etc are executable binaries in its default search path :D

---

