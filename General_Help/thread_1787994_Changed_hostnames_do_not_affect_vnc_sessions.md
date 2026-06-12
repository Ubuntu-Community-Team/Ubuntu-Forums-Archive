---
title: "Changed hostnames do not affect vnc sessions"
date: 2011-06-21
forum: General Help
---

### Post by dwasifar on 2011-06-21
I changed the hostnames of my servers and clients.  They know their new names, except in vnc.  When I vnc into a server from a client, the vnc session displays the old hostnames for both machines.

I'm sure either vino (on the server) or xtightvncviewer (on the client) is storing history and using the old names from it.  How do I clear it out and start fresh?

---

### Post by crispy_420 on 2011-06-22
How did you change the hostnames? Command line or file edit?

---

### Post by dwasifar on 2011-06-22
File edit.  I changed /etc/hostname, grepped through /etc and its subdirectories to find instances of the old name and changed those.  Ran /etc/init.d/hostname restart to apply.

The machines know their new names.  If you open a terminal you get [user]@[newname] as the prompt.  Likewise system monitor.  But if I connect to a remote machine I get the old name.

It has to be coming from the client.  Right now I'm VNCed in to a machine running from liveCD, and the session still has the client's old name.

---

