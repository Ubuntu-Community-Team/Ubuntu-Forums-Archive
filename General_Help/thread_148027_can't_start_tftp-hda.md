---
title: "can't start tftp-hda"
date: 2006-03-21
forum: General Help
---

### Post by ento on 2006-03-21
Hi

I can not start tftp-hda, when i type /etc/init.d/tftp-hda start nothing is happining.
I do not have any tftp conf file.

I am doing a ltsp installation and when the client is booting it says tftp....
What is wrong?

---

### Post by schilcha on 2006-03-21
I do have a proper tftp-hpa (hope you're talking about that one) installation here. As far as I remember, tftpd assumes to be controlled by an inet-daemon by default. I don't have any, since it wasn't swooshed up onto my system when installing ubuntu. 

So, what I did was editing the tftpd-configuration to make it run on its own. Here's my /etc/default/tftpd-hpa file:
```

#Defaults for tftpd-hpa
RUN_DAEMON="yes"
OPTIONS="-l -s /var/lib/tftpboot"

```

I've no idea, if it's good style to edit the /etc/default/-files. Right now, I couldn't care less -- it works.

---

### Post by Jose Catre-Vandis on 2006-09-02
Thanks, this setting helped me get my ltsp setup going again. Don't know why it stopped working but, hey, changing
```
 RUN_DAEMON="no"
```
to
```
 RUN_DAEMON="yes"
```
did the trick

---

