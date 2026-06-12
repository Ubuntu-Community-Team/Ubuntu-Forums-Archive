---
title: "remote lock will not work on multi-vid card ubuntu studio box"
date: 2011-02-11
forum: General Help
---

### Post by jeebustrain on 2011-02-11
I'm trying to set up some scripts from one machine that I can use to remotely lock all of my workstations remotely. I have a virtual ubuntu machine ported out to the internet w/ ssh open and I'm using ServerAssistant on my droidX phone to kick off the scripts. I have all of my ssh keys shared between the boxes so I don't have to log on. 

Everything works beautifully for one machine, a regular Ubuntu 10.10 box with a single video card with 2 monitors. This is the script contents:
```

ssh -X brainstem@zappa "export DISPLAY=:0; gnome-screensaver; gnome-screensaver-command -l"

```

But my other desktop, a triple monitor ubuntu studio 10.04 box (2 vid cards) will not kick off with the same syntax as above (obviously different computer name). If I execute the command manually from the remote machine, it doesn't work either. Just to make sure, I ran "gnome-screensaver-command -l" locally on this box just to make sure that part works - it locks the machine locally just fine. I just can't seem to get it to work from another machine. I've tried from 2 different boxes and have the same results. I can do anything else I want over ssh and it all works. 

my google-fu doesn't seem to be working very well tonight.

---

### Post by jeebustrain on 2011-02-13
nobody has an idea?

---

