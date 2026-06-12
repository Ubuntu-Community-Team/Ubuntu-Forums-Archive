---
title: "System force check fails, root password forgotten"
date: 2009-11-06
forum: General Help
---

### Post by amallory on 2009-11-06
Slight problem here, and I am sorry if this has been answered already and I didn't find it, but I hope somebody can help. I'm no stranger to Linux, Debian user myself, but I don't consider myself the best at it either.

A while ago I convinced my own mom to give up Windows for Linux, and all was well up until now when the system upon booting forces a system check which fails. After this, I am prompted to enter a password so I can manually run a fscheck check. Problem is, you guessed it, nobody remembers the stupid root password. There are two other accounts with full sudo rights, but it doesn't do me any good if I can't login. I would try to replace the md5 for the root in the shadow file, but I don't have another computer that can help me with this at the moment.

Any help would be greatly appreciated!

---

### Post by falconindy on 2009-11-06
Because Ubuntu has no root account, that prompt should be asking for the password for UID 1000, which is the first user created (when you installed). Likely your mom's account?

Short of that, boot off of a liveCD, and just run 'fsck' for each partition. That should let you boot normally.

---

### Post by amallory on 2009-11-06
GAH! I totally forgot about the live cd. I really hope that i can find one cause I can honestly say this is the only time I wish I didn't have a netbook... I suppose I can install some version of linux onto my flash drive though, only 500MB so Ubuntu is out of the question as far as thats concerned.

Thanks for the response!

P.S. Does Ubuntu not have a root account peroid? If I remember correctly it just leaves root as an account without a password and can't be logged in. I'm sure I changed that if that is the case. Also I tried the password for both accounts and several others before I even posted, sorry I didn't post that in the first post.

---

### Post by falconindy on 2009-11-06
If you wanted to get technical, the root account does exist (it has to), but its disabled as far as being able to log into it interactively.

---

### Post by amallory on 2009-11-06
yea, I remember the first day I switched to Linux, Ubuntu was the first distro I used and I was somewhat annoyed about not being able to log in at the welcome screen as root. I also think I found an article showing me how to disable that feature and then proceeded to pretty much destroy the installation. Thanks for your help and speedy responses, got it taken care of now.

---

