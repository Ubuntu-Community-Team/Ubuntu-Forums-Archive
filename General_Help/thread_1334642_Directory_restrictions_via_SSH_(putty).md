---
title: "Directory restrictions via SSH (putty)"
date: 2009-11-22
forum: General Help
---

### Post by necrolite on 2009-11-22
Hey all. 

I have a (hopefully) simple question. 

currently, a friend has gone to university, and ive agreed to give him a login for my server, so that he may tunnel out and play a few select online games that otherwise wouldnt work. 

ive created a login for him, but currently that login would allow him to nose around the system and see whats in different folders. my question is, how can i modify his login so that he can still use putty to create an ssh tunnel out of his universities network, but so that he is restricted to his home directory? as far as denying ftp access goes, im up to speed on that. just this one thing thats bugging me! 

as far as the system goes, its running on ubuntu 9.10

ps, this seemed the most appropriate section, feel free to move, i couldnt find anything specific.

---

### Post by scorp123 on 2009-11-22
You could give him a **"nologin"** shell. What I mean is this: Usually a user gets e.g. **/bin/bash** as a login shell. They connect via SSH and that is the shell that gets fired up.

But "bash" isn't the only shell. There are two shells that will deny a login: **/bin/false** and **/usr/sbin/nologin**

So you could give him an account .... but make sure he gets e.g. **/usr/sbin/nologin** as his "shell"

Now ... despite this he'd still be able to use SSH! On Linux you'd now have to use "ssh" with the "-N" parameter.

On Putty for Windows the parameter is called:
***Category > Connection > SSH > [x] Don't start a shell or a command at all***

So SSH tunnelling and using your server as proxy would still work ... but logging into an actual shell would not and would be refused. He can establish a tunnel ... yes. But not get a shell prompt and snoop around.

I guess this is what you want?

.
.
.

---

### Post by necrolite on 2009-11-22
that's exactly what i was after! i'd rather not have him be able to see anything, but use it purely to tunnel. thanks, ill pass this info on to him :)

---

