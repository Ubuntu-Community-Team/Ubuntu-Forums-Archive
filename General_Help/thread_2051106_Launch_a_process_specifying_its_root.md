---
title: "Launch a process specifying its root"
date: 2012-09-01
forum: General Help
---

### Post by firedragon1 on 2012-09-01
Hi all. I'm new to this forum (so if it's the wrong place to make this question, forgive me).
What I'm going to ask you is if it's possible to launch a process from the terminal (in my case, I want to launch the erlang shell) specifying a folder and letting this process believe that there isn't anything over it. Like this folder is the root.
Any suggestion?
Thank you :-)

---

### Post by Nytram on 2012-09-01
Hi welcome to these forums. There's a command called **chroot** (change root) which I believe does what you want. You can find more info on it by doing a **man chroot.** I've never needed to use it before myself, but I think it lets you execute a command and specify any folder to act as the root folder.

---

### Post by dcstar on 2012-09-01
> **firedragon1 said:**
> Hi all. I'm new to this forum (so if it's the wrong place to make this question, forgive me).
What I'm going to ask you is if it's possible to launch a process from the terminal (in my case, I want to launch the erlang shell) specifying a folder and letting this process believe that there isn't anything over it. Like this folder is the root.
Any suggestion?
Thank you :-)

Ignore that first response, it does not understand what you want.

Simply make a script that has a "cd" command to the absolute folder path you want to run the script in, and then the command to run the process.

---

### Post by firedragon1 on 2012-09-03
Thank you guys ;-) I'll try these solutions!

---

