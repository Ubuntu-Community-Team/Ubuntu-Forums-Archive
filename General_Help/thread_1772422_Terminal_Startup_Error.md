---
title: "Terminal Startup Error"
date: 2011-05-31
forum: General Help
---

### Post by GreenRaccoon on 2011-05-31
I've got a weird problem.  When I open up Terminal, it always says this at the top:

```
bash: /tools: Permission denied
```

I can still do everything I need/want to do in Terminal but it's just a little annoying.

I thought it might be a bad flag on the command, so under /usr/share/applications, I checked the properties of the Terminal application. The command is just "gnome-terminal" like it's supposed to be.

I've searched the Internet and can't find anything.  Anyone have an idea?

---

### Post by DaithiF on 2011-05-31
Hi, the problem won't be the application (gnome-terminal) that runs, it will be the shell (bash) that runs inside that terminal.  Have you made any changes to the bash profile files on your system?  This could be any of the files: .profile, .bash_profile, .bash_login, .bashrc in your home directory, or the system-wide files /etc/profile and /etc/bash.bashrc

---

### Post by GreenRaccoon on 2011-05-31
Fixed!  I remembered that when I was playing around with android sdk I added this to my .bashrc file:

```
export PATH=$PATH:home/usr/android-sdk/tools
```

I just deleted it and it's fixed.  Thanks DaithiF!

---

