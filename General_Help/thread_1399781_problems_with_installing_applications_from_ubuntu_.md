---
title: "problems with installing applications from ubuntu software center"
date: 2010-02-06
forum: General Help
---

### Post by da1337ninja on 2010-02-06
I'm having problems with the ubuntu software center. When I try to install any software it does nothing when I click the install button. I can click on the visit website page and download the source and compile it manually but I was under the assumption that you could use the install button and it would do it automatically for you. Am I wrong? I am running UNR 9.10 on an Acer Aspire One 110-1588. Thank you very much.

---

### Post by zeroseven0183 on 2010-02-06
I'm not sure what others may think but you can try reinstalling Ubuntu Software Center from Synaptic. Open Synaptic, look for software-center and re-install it. Be sure Ubuntu Software Center is closed.

Question: What application are you trying to install? Have you tried using apt-get in Terminal or installation via Synaptic?

---

### Post by zeroseven0183 on 2010-02-06
You should also try the procedure mentioned in this thread: [Ubuntu Software Center "Install Button" not working]("http://ubuntuforums.org/showthread.php?t=1340014&page=2").

Check to see if the 'Unlock' button in System > Administration > Login Screen is clickable. If not, as mentioned in the above thread, it's a keyring problem.

---

### Post by warfacegod on 2010-02-06
Try this:

Right click your Applications menu and select Edit Menus. Highlight Ubuntu software Center and click properties on the right. In that window, change the Command:

From:

```
/usr/bin/softawre-center
```

To:

```
gksudo softawre-center
``` (note the space)

---

### Post by da1337ninja on 2010-02-07
Thanks for the solutions. I'll try them all out and report back the one that works. :) I'm still a little confused on why this happened. I'm not super linux savvy nor have I been using it forever, but this has never happened to me before.

---

### Post by blueshiftoverwatch on 2010-02-07
What exactly is the purpose of the software center? I've looked through it and everything that's in there you can get from apt-get/synaptic.

---

### Post by florus on 2010-02-07
Its is a simple gui method which is easier for ex-windows converts.

---

### Post by warfacegod on 2010-02-07
> **blueshiftoverwatch said:**
> What exactly is the purpose of the software center? I've looked through it and everything that's in there you can get from apt-get/synaptic.

The long term goal is to replace Update Manager, Add/Remove (did that already), and Synaptic. I think Software Sources and few other things are supposed to get rolled into it as well.

---

