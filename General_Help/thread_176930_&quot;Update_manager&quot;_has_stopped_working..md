---
title: "&quot;Update manager&quot; has stopped working."
date: 2006-05-15
forum: General Help
---

### Post by chris_andrew on 2006-05-15
Hi,

My Update Manager was working fine until recently.  I have just done:

su -
(passwd)
apt-get update
apt-get upgrade -u

and downloaded 3 updates.  

Can anybody tell me why "Update Manager" failed to tell me?

Many thanks,

Chris.

---

### Post by chris_andrew on 2006-05-16
Anybody got any ideas?

---

### Post by Irony on 2006-05-16
Not really. But when I clicked to update these they didn't update. After clicking several times I got;

[PHP]NOT AUTHENTICATED

 mysql-common
 libmysqlclient12
 libmysqlclient14  [/PHP]

I therefore went to synaptic and updated them.

I'll have to see when more updates come along whether update manager will update them.

---

### Post by chris_andrew on 2006-05-16
Hmmm,

In my */etc/apt/sources.list* I have 2 sources that aren't official, and get a similar problem, but i'm sure Update Manager worked up until recently.

Anybody else experienced this?

Maybe I should stick to the old-fashioned manual way to update.

Cheers,

Chris.

---

### Post by Fleaman13 on 2006-05-16
I have some issues with update manager as well... I get:

W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_breezy_._Packages) - stat (2 No such file or directory)

I think this is simple to fix, but my head hurts right now after dealing with the wireless card issues I was having... any thoughts? :)

---

### Post by The J on 2006-05-16
Hmm...lately when I click on the update icon, the manager just looks like it's doing a refresh (Reload in Synaptic or apt-get update).  The icon will stay in the busy state for a minute  or so and then return to orange with nothing updating.

Running apt-get update and apt-get (dist-)upgrade does work fine, though.

---

### Post by chris_andrew on 2006-05-16
I'm not even getting an icon in my "system tray". 

When I do *ps -ef | grep manager*, no sign of update manager running.  I verified this by starting it manually from the System/ Admin menu, and the same *ps* command confirmed that it was running.  This possibly suggests that Update Manager is no longer running automatically.  I should add, that my system is fully upto date.

Chris.

---

### Post by Irony on 2006-05-16
It looks like some of the recent updates have disabled the update manager from actually updating - hopefully more updates will solve this!

---

