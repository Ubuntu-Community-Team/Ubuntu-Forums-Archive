---
title: "Yet another &quot;no tty present and no askpass program specified&quot;"
date: 2012-07-15
forum: General Help
---

### Post by filosophem on 2012-07-15
Hello all,

I have a little problem with the script mount.sh found [here]("http://ubuntuforums.org/showthread.php?t=87369") (lazy way of mounting an iso file).

My problem is that the directory in /media is never created. I modified the line " *sudo mkdir /media/"$*"* " to " *sudo mkdir [COLOR="Red"]**-v**[/COLOR] /media/"$*" [COLOR="red"]**2> /home/username/log**[/COLOR]* "

I found this in the log: "sudo: no tty present and no askpass program specified"

Of course I did try many things (reinstall sudo, revert to an old version, modify the sudoers file. There are many threads talking about the no tty problem)

Since nothing seems to work, can anyone give me an idea of the next step (if any)? 


Ubuntu version 11.04
kernel verion 2.6.38-15-generic
GKsu version 2.0.2
Sudo version 1.7.4p4

---

