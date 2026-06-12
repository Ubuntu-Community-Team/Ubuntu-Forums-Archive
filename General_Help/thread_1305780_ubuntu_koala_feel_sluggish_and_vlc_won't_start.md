---
title: "ubuntu koala feel sluggish and vlc won't start"
date: 2009-10-30
forum: General Help
---

### Post by yotama9 on 2009-10-30
Hi guys. 

I've installed ubuntu koala over my ubuntu jaunty (reforamat the partition).

Everything was fine with the old distro but the new distro feels sluggish. It take the system something like half a second to response to my mouse clicks and the animation isn't soothed. 

Also, VLC won't start. system monitor indicate vlc is running but there is no gui. I have an intel graphic card (I'm not sure of it's model I can check if you think it's relevant). 

Here is the output when I try to run VLC:

```

VLC media player 1.0.2 Goldeneye
[0x9ec2058] main interface: creating httpd
[0x9ed2c40] main interface error: no interface module matched "globalhotkeys,none"
[0x9ed2c40] main interface error: no suitable interface module
[0x9e13140] main libvlc error: interface "globalhotkeys,none" initialization failed
^C[0x9e132d8] signals interface error: Caught Interrupt signal, exiting...


```

Thank you

Yotam

---

### Post by pro003 on 2009-10-30
you have a bad rep video card... did you tried installing drivers for your video card? maybe that will help...

---

### Post by P4man on 2009-10-30
> **pro003 said:**
> you have a bad rep video card... did you tried installing drivers for your video card? maybe that will help...

No that wont help, as he has intel video, the drivers are right in the kernel. Not that I have a proper solution for him though...

---

### Post by pro003 on 2009-10-30
> **P4man said:**
> No that wont help, as he has intel video, the drivers are right in the kernel. Not that I have a proper solution for him though...

i meant "a video card with bad reputation" not repository... well xcuse me for not finishing all the words i type

---

### Post by yotama9 on 2009-11-02
As for the VLC problem. Turn out that I have defined VLC to listen on the 8000 http port (my iPod) and for some reason it caused it to crash. 
This listen thing is a leftover from my old ubuntu. 

Thanks.

---

