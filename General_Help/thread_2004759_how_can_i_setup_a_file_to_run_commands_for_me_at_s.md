---
title: "how can i setup a file to run commands for me at startup"
date: 2012-06-16
forum: General Help
---

### Post by mcwolves32 on 2012-06-16
i need too have synclient areabottomedge=3900 to run at startup so it doesnt mess my touchpad up anyone got some insight?

---

### Post by ajgreeny on 2012-06-16
> **mcwolves32 said:**
> i need too have synclient areabottomedge=3900 to run at startup so it doesnt mess my touchpad up anyone got some insight?
Make an executable shell script called **touchpad** (or any name you prefer) with the following contents
```
#!/bin/bash
synclient AreaBottomEdge=3900
```making sure you get the upper case letters right or it won't work, and point to that in your startup applications list.

---

### Post by kjohri on 2012-06-18
You can use an Upstart script to run the command. The following link gives more details,

[http://www.softprayog.in/tutorials/starting-linux-services-with-init-scripts]("http://www.softprayog.in/tutorials/starting-linux-services-with-init-scripts")

---

### Post by ajgreeny on 2012-06-19
> **kjohri said:**
> You can use an Upstart script to run the command. The following link gives more details,

[http://www.softprayog.in/tutorials/starting-linux-services-with-init-scripts](http://www.softprayog.in/tutorials/starting-linux-services-with-init-scripts)
I never did understand the upstart way of doing things, and I'm afraid I have to say that your link has not helped me one small step in that direction.

It all seems so much more complicated than using a self written, simple, one line script.

Perhaps I am missing some important point about using upstart, but I stil think my script way to do this is much easier.

---

