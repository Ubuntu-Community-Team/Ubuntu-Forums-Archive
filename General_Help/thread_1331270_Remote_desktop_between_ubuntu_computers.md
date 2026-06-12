---
title: "Remote desktop between ubuntu computers?"
date: 2009-11-19
forum: General Help
---

### Post by becarexinxin on 2009-11-19
i all~ I am trying to connect my desktop ubuntu from my labtop ubuntu, I allowed "remote desktop" of the desktop ubuntu, and using "terminal server client" and vnc protocol on my labtop for the connection, but my labtop screen is 1024*768, desktop is much larger, it is difficult to navigate the remote desktop. I  found online help saying that I should modify vnc server configuration on my desktop at /etc/sysconfig/vncservers to specify the geometry as 1024*768, but there is no such file on my desktop. Can anyone help me out here?  Thanks a million~

---

### Post by Aubergines on 2009-11-19
Isn't there a "Display" tab on the terminal server client that allows you to change the resolution?

---

### Post by nothingspecial on 2009-11-19
For remote desktop I prefer xrdp.

That said I just use ssh with -X

---

### Post by becarexinxin on 2009-11-19
"display" does allow you to change the size of remote desktop, but my desktop has a bigger screen than my labtop, even I do "full screen" with "display", my desktop screen won't fit into my laptop screen....

So my question is how could I specify on my desktop computer I am going to use 1024*768 labtop to connect to it,  thus it always show as 1024*768 in the remote connection.

Thanks,

---

### Post by becarexinxin on 2009-11-19
To [nothingspecial]("http://ubuntuforums.org/member.php?u=491516"), I tried xrdp, it still has a screen size problem....  I couldn't fit my big desktop screen into my small labtop screen, which is really painful....

---

### Post by nothingspecial on 2009-11-19
I`m going to sleep right now.

But, what do you want to do with the remote desktop?

There may be an easier solution.

---

### Post by becarexinxin on 2009-11-19
I just switched from windows to linux,  I used to have both my desktop (at school) and labtop(at home) installed windows, so when I am at home, I will just remotely connect to my desktop at school to continue my work. I want to do the same with linux....

---

### Post by nothingspecial on 2009-11-20
In that case, I recomend using ssh. Have a look at [[COLOR="Magenta"]this guide[/COLOR]]("https://help.ubuntu.com/community/SSH").

You need to access your remote machine using the -X argument if you want to run graphical apps. So say you wanted to continue an essay using abiword on your remote machine, type

```
ssh -X user@ipadress
```

Then type ```
abiword
``` and you will be running it on your remote machine.

Once you`ve got it configured, if you want to browse files, go to your places menu and choose "connect to server". In the first box choose ssh. In the second put user@ipadress. Tick (check) the box next to add bookmark and give your remote machine a name. Then any time you want to access your homework files on the remote machine you can do it from your places menu.

---

### Post by becarexinxin on 2009-11-20
hi [nothingspecial]("http://ubuntuforums.org/member.php?u=491516"),

Thanks so much for the detailed explanation. I followed your suggestion, and it worked well.

I guess I just need to adjust to linux in a way that I do things in a linux way, rather than finding substitute softwares for windows all the time~

Best,

---

### Post by nothingspecial on 2009-11-20
Glad to be of help :D

---

