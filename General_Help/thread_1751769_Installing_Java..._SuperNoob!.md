---
title: "Installing Java... SuperNoob!"
date: 2011-05-07
forum: General Help
---

### Post by Majoron on 2011-05-07
Hello, I'm undoubtedly inept at what I'm doing. Part of it is from lack of experience, part of it is from lack of sleep, but hey, that's neither here nor there.

Basically I'm trying to install java on my vps. I'm using Putty and assuming SSH is something relevant. LOL

Anyways, I want to run a minecraft server. I've gotten it setup, downloaded, unzipped, along with my map and the only thing I need to do now is install java.

Simple, right? An easy "yum install java-1.6*" and I'd be on my way, or so I thought. Apparently yum isn't a command. Certainly not yummy. 

Can anyone point me in the right direction? Also, if it's not too much to ask, a little bit of explanation goes a long way. So far I've found a great quantity of commands shoved in my face but no real explanation what any of them mean or do. So, if you do know what it is that I'm missing, please, could you tell me what that is, instead of just telling me the command I'm looking for. Or, the command works too. :P


The server is running Ubuntu 9.10 Gnome+VNC template --if that helps at all

---

### Post by Paddy Landau on 2011-05-07
Ubuntu doesn't use yum. It uses apt-get instead.

Try these two commands instead:
```
sudo apt-get update
sudo apt-get install java-common icedtea6
```

---

