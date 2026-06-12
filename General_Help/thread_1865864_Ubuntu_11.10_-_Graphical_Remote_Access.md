---
title: "Ubuntu 11.10 - Graphical Remote Access"
date: 2011-10-20
forum: General Help
---

### Post by trivialpackets on 2011-10-20
What is the best way to be able to remote into your ubuntu 11.10 box.  I had been using NX, but it was not behaving well at all with Unity.  

VNC could be done I'm reasonably sure, but performance wise, that has always been worse for me, maybe it's better now?  It's been a while.

Ideally a remote-desktop like with solid performance would be great.  Anyone with any experience with this?

---

### Post by spiky001 on 2011-10-20
Have a look at Remmina it,s in the repos, Have you tried X over ssh

---

### Post by trivialpackets on 2011-10-20
I am going to try X over ssh tonight, I was just reading on it.

Is Remmina a server or a client?  I am connecting from a windows PC using putty if I go over ssh, but I will be trying later tonight.

---

### Post by spiky001 on 2011-10-20
Cant help you with windows I only use ubuntu, I think tight vnc from windows

---

### Post by trivialpackets on 2011-10-20
The windows part isn't my issue (well it's an issue, but it is what it is :) ), it's a matter of looking to see what others are using for remote access if anything.

---

### Post by spiky001 on 2011-10-20
[http://en.wikipedia.org/wiki/TightVNC](http://en.wikipedia.org/wiki/TightVNC)

---

### Post by gunksta on 2011-10-20
VNC, TightVNC, etc. are all, in my experience, more or less that same thing. I would be surprised if any VNC out-performed NX. SSH over X has the advantage of letting you only run the apps you want from the remote box. In other words you don't run the remote desktop, you run the remote apps.

Why are you trying to get remote graphical access to your computer. I'm not being nosy, I'm trying to see if there is some other way to accomplish what you are trying to accomplish and understanding what you are trying to do might help.

---

### Post by trivialpackets on 2011-10-20
I have a dev box at home that is my main box that I run ubuntu on.  When I'm not at home and have time to do some work, then I like to be able to have access to the box.  I can work with vim over ssh if need be, which is why there is no real urgent need this second, but I was curious what others experience is solving this problem.  If I'm able to get the ssh over X working, I'll be all set, that would be ideal most likely.

---

### Post by trivialpackets on 2011-10-21
Issue resolved for me. I went back to play around with NX and found that by setting the NX client to load custom and then run the command:

gnome-session --session=ubuntu-2d

with New virtual desktop selected, I was able to connect.

---

