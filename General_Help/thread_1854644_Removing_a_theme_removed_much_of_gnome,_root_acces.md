---
title: "Removing a theme removed much of gnome, root access broken"
date: 2011-10-04
forum: General Help
---

### Post by circuit_bent on 2011-10-04
Hello!

So I did a dumb thing today. I wanted to remove gtk2-engines-murrine from my machine, which I had installed to get clear windows. Problem is, when I removed it said it was removing a few gnome packages (I used sudo apt-get remove gtk2-engines-murrine). I figured that they were either not needed, or more likely that I could reinstall them if it did anything crazy...

Well I was wrong. Now after I log in, I have no permission to do anything. I can't ls. I don't even have permission to give myself permission. Some examples:

ls
*ls: cannot open directory .: Permission Denied*
su
*setgid: Operation not permitted*
sudo ls
*sudo: unalbe to change to sudoers gid: Operation not permitted*

Any advice on how I can regain access and then restore what I messed up? I'm not sure what packages I ended up removing, but I know that some of my visual styles are gone.

Thanks so much.

---

### Post by 3Miro on 2011-10-04
Try booting in safemode and then reinstall ubuntu-desktop.

---

### Post by circuit_bent on 2011-10-04
Awesome. That completely fixed it. Thanks much :)

---

