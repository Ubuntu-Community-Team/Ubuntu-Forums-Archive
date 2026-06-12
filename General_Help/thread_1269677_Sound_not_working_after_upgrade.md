---
title: "Sound not working after upgrade"
date: 2009-09-18
forum: General Help
---

### Post by chaotzu on 2009-09-18
Hey just upgraded to newest version of Ubuntu and now my sound isn't working at all. It recognizes that I have a sound card and the device and all. In alsa it says I can set the volume level and I have made sure that it is not muted but I'm not getting sound from anything. 

It says my codec is Realtek ALC1200 and Generic 10de NVIDIA MCP78 HDMI, any suggestions of what I can do to fix the problem?

Thank you

---

### Post by Liolikas on 2009-09-18
Hmm try to reboot into older kernel (on boot like 2.6.25 and 2.6.26 etc.) use not biggest number and see if helps.

---

### Post by chaotzu on 2009-09-18
> **Liolikas said:**
> Hmm try to reboot into older kernel (on boot like 2.6.25 and 2.6.26 etc.) use not biggest number and see if helps.

This does get my sound to work. Should I just keep using this older kernel?

---

### Post by Liolikas on 2009-09-18
Yes. 

You can compile new custom kernel, but not worth that work I think. Unless huge security problems etc. with old.

And you can help Ubuntu and others and post Ubuntu bug-regression to launchpad with your card model. 

Team will fix things with next update. They simply overdid clean up job like always. :P

---

### Post by chaotzu on 2009-09-18
> **Liolikas said:**
> Yes. 

You can compile new custom kernel, but not worth that work I think. Unless huge security problems etc. with old.

And you can help Ubuntu and others and post Ubuntu bug-regression to launchpad with your card model. 

Team will fix things with next update. They simply overdid clean up job like always. :P

Thanks and will do, but where is launchpad >.<;

---

