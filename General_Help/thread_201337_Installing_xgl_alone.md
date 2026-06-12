---
title: "Installing xgl alone"
date: 2006-06-21
forum: General Help
---

### Post by bohboh on 2006-06-21
I installed cairo-clock to see what it was like, there is a black border around the clock. To fix this i need xgl installed, i already have but under another session. I need my system for work so i didnt want it to affect things so decided to have it on another session.

My questions is, if i have already installed xgl/compiz on another session, is there a way i can enable just xgl for my default gnome session? do i have to reinstall xgl in my default gnome session?

If so, i followed [this guide]("http://www.ubuntuforums.org/showthread.php?t=127090") but got stuck when all links to xgl-svn_100.tar.bz2 were broken.

How do i simply install xgl on its own in my default gnome session and will it break/make my system unstable.

Thanks :)

---

### Post by grendelkhan on 2006-06-21
You run it from gdm in place of a normal X server, you can't really set it to only come on if you log in.

You could, if you wanted, shut down gdm and then just as yourself run the start xgl script.  

A better howto is in the pinned thread in this forum, you can get Xgl and Compiz installed right from apt.

---

