---
title: "(unreachable) from \w in $PS1"
date: 2011-09-19
forum: General Help
---

### Post by JustisS on 2011-09-19
For some reason whenever I create a new shell in byobu over ssh, instead of 
```
justis@hellhouse/$
```
i get 
```
justis@hellhouse:(unreachable)/$
```
What is this, and how do I fix it? When I installed the server (ubuntu 11.04), i did choose the mail option, but I think I removed it by purging postfix. I don't know if that's the problem, or how I can fix this. I'd also like to completely wipe out (if not already)/perhaps reinstall the mail thing properly (ocd).
Here is the result from echo $PS1:
```
${debian_chroot:+($debian_chroot)}\u@\h:\w\$
```
Could it have something to do with my hosts file? This is driving me crazy!

---

### Post by JustisS on 2011-09-20
Bump. This is driving me insane.

---

### Post by patryk77 on 2011-09-20
Sounds like it has something to do with your path...

What does:
pwd
say?

---

### Post by JustisS on 2011-09-20
Pwd just says the same, 
```
(unreachable)/
```
or for example when I'm in a directory,
```
(unreachable)/programming
```

---

### Post by patryk77 on 2011-09-20
what folder are you in before you start byobu?

What does ls -al give you for . and .. ?

---

### Post by JustisS on 2011-09-20
drwx------ 8 justis justis 4096 2011-09-16 23:26 .
drwx------ 8 justis justis 4096 2011-09-16 23:26 ..

I'm not sure what directory, I have byobu set to run at startup when I connect. I don't have physical access to the computer, so I only connect via ssh.

---

### Post by patryk77 on 2011-09-20
Sounds like whatever it is it's related to the path, either something to do with permissions or maybe you chroot on connection...

The easiest way to fix this might be 
export PS1='${debian_chroot:+($debian_chroot)}\u@\h:\W\$'

Replacing \w with \W would make it print just the current directory instead of the whole path (hopefully skipping the unreachable bit).

If that helps and you don't mind having it like that, try to change it in your .bashrc file if you have access to it.

While you're playing with that, you can always [pimp it out](http://glog.procrasstination.com/index.php?/archives/12-Pimping-the-BASH-Prompt.html) too ;)

If that still doesn't help (and it might not at least in the directory you start in), I am not sure what to tell you :\

---

### Post by JustisS on 2011-09-20
It did help, but as I do a lot of my schoolwork in several directories to try and stay organized, I'm afraid that solution isn't going to work for me :\ thank you for your help though!

I'll keep searching/hope someone else who knows how to fix this can help.

Thanks again :)

(i googled something and was excited and thought i found the solution, then i realized it was this thread :()

---

