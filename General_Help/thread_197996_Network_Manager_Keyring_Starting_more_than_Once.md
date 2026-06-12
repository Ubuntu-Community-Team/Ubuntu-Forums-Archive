---
title: "Network Manager Keyring Starting more than Once"
date: 2006-06-16
forum: General Help
---

### Post by penguinmaster on 2006-06-16
When I first login to gnome the network manager keyring dialog comes up asking my password.  Lately though, that dialog box comes up multiple times and if I put in my password to unlock the keyring, and cancel out of the other boxes it won't connect to my access point.  I have try to connect through the applet then instead.  My question is there a way to have it not show up multiple times, or not show up at all.  

Thanks

---

### Post by cwmaxson on 2006-06-16
Download the Keyring Manager Gui.  There you will probably see that there are multiple passwords being stored.  Each one delivers a popup screen on startup.  If you want less popups you might want to disable the passwords you don't use on every startup.

---

### Post by penguinmaster on 2006-06-16
[QUOTE=cwmaxson]Download the Keyring Manager Gui.  There you will probably see that there are multiple passwords being stored.  Each one delivers a popup screen on startup.  If you want less popups you might want to disable the passwords you don't use on every startup.[/QUOTE]
Thanks for the tip cxmason.  ALthough when I start that app up, it only shows the one password and that's all.  Any other suggestions?

---

### Post by popkid on 2006-06-18
I have this exact problem, posted two or three days ago now, but got no replies...

This used to work fine, I got one pop-up, entered password and all was good

Recently though I started to get 2 and then 3 pop-up boxes....

Getting really fed up with this now, as it seems to matter which order I complete the boxes... sometimes network manager is working fine after completing one... there are 2 left... if I fill the password in for them the wireless bars go off and I have to reconnect, if I just close the request box, the network icon switches to disconnected... leave the boxes on the desktop though and everything works fine... daft...

Keyring manager shows only one key so what is going on?

pK

---

### Post by penguinmaster on 2006-06-18
popkid,

  Now when I start up my laptop everything is normal.  Not sure what happened.  it started for me once I started switching between two wpa protected networks.  Not sure if that helps at all. I haven't been back to the other wpa protected network so maybe that has something to do with it, not sure.

---

### Post by popkid on 2006-06-18
[QUOTE=penguinmaster]popkid,

  Now when I start up my laptop everything is normal.  Not sure what happened.  it started for me once I started switching between two wpa protected networks.  Not sure if that helps at all. I haven't been back to the other wpa protected network so maybe that has something to do with it, not sure.[/QUOTE]

Hmmm... don't think that would be the root of my problems, I only have one network... there is another wpa protected network in range (belonging to a neighbour) but that has always been there and as I said, it used to work fine.

I'll let you know if I manage to sort it out

pK

---

### Post by luopio on 2006-07-18
So any progress on this issue? I'm still suffering the same problem. I'm on a WEP-protected network and I mostly get two or three dialogs on startup. Sometimes it works correctly and asks the keyring password only once.

---

### Post by luopio on 2006-07-18
Hmm.. this seems to be resolved in 0.6.3: 
```
* src/NetworkManagerPolicy.c
- (nm_policy_device_change_check): don't switch devices if the "best" AP is
 essentially the same as the current activation request, but the current 
activation request isn't done activating yet.  Fixes multiple requests for 
keyring password on startup for Gnome applet. Gnome.org #341297
```
([http://mail.gnome.org/archives/ftp-release-list/2006-June/msg00014.html](http://mail.gnome.org/archives/ftp-release-list/2006-June/msg00014.html))

Now I'll only have to look for the debs :-k ..

---

### Post by popkid on 2006-08-02
Still asks twice or three times for me...

What did you install as a fix?

pK

---

### Post by luopio on 2006-08-03
> **popkid said:**
> Still asks twice or three times for me...

What did you install as a fix?

pK

You're running 0.6.3? Should be fixed there. I see that Edgy is using the that version.. I guess I'll update to it someday.

---

### Post by popkid on 2006-08-03
Ah no sorry, I'm using 0.6.2... I'll keep waiting eagerly for the backport!

pK

---

