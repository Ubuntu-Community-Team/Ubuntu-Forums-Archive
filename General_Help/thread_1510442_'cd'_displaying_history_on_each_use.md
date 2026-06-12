---
title: "'cd' displaying history on each use?"
date: 2010-06-15
forum: General Help
---

### Post by williane on 2010-06-15
Can someone explain why my directory history is being displayed after each use of the 'cd' command. After about an hour the list is filling up my window. TIA

---

### Post by whiskeylover on 2010-06-15
Paste the output of "echo $PS1"

---

### Post by williane on 2010-06-15
${debian_chroot:+($debian_chroot)}\u@\h:\w\$

---

### Post by linux-hack on 2010-06-15
do you have an alias for the cd command ? look in the .bashrc or .profile file.

I hope for you that you don't have a rootkit on your system if there is no alias and you didn't change the action of this command..

---

### Post by williane on 2010-06-15
I found "alias cd="pushd"" in /home/me/.bash_aliases 

I didn't notice this until today, although I had not used this server in a few days. I asked around and no one has made any changes that we think could have caused it. 

Is this a default setting? I'm 99% sure it wasn't doing this before as I'm sure I would have noticed. 

Anyways, I commented out that alias and everything looks good now. 

Thanks

---

### Post by linux-hack on 2010-06-17
If I war you I'd start doing a scan of my system ...

---

### Post by linux-hack on 2010-06-17
Dont rely know if your a beginer but here is a good thing to learn : [http://www.linuxtopia.org/LinuxSecurity/index.html](http://www.linuxtopia.org/LinuxSecurity/index.html)

---

