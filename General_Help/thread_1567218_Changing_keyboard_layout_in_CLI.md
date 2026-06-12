---
title: "Changing keyboard layout in CLI"
date: 2010-09-03
forum: General Help
---

### Post by lz1dsb on 2010-09-03
OK, so here's the situation basically. 
I have an Ubuntu server running on a VM. I'm accessing this system mainly remotely, and usually with a console connection. I export the output of some applications (like Skype, Google Chrome etc.) to my Windows desktop, where I run Xming as my X server. Everything works pretty neat, but... I can't change the keyboard layout, because the applications are running on the remote machine. So is there a way to change the keyboard layout in CLI?

Cheers, 
Boyan

---

### Post by VCoolio on 2010-09-03
The command is setxkbmap but I don't know if that works on remotes.

---

### Post by lz1dsb on 2010-09-03
Interesting, I'll give it a shut...

---

### Post by lz1dsb on 2010-09-04
This really works. And it changes the layout of the cli. I haven't test it though with an application. I mean, when I start an application, does it use the keyboard layout or it starts with the default? I need to check it...

Cheers, 
Boyan

---

### Post by lz1dsb on 2010-09-04
It works on applications also. So when I execute for example 
setxkbmap -layout bg
the layout is changed in all applications. I actually expected a different behavior as I've checked the checkbox "Separate layout for each window" in the Keyboard Preferences...
And also when I used it, my standard key for alternating the different layouts wasn't working anymore :p 
Well I guess I have to dig a bit deeper into the manual, probably there're some other options...

---

### Post by lz1dsb on 2010-09-04
Yeah, it works from remote :D It's solved, well it's not that flexible, but for me it's fine...

Cheers, 
Boyan

---

