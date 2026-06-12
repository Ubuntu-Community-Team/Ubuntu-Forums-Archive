---
title: "Noob just screwed up his unity desktop, HELP"
date: 2012-01-02
forum: General Help
---

### Post by littleport2003 on 2012-01-02
Total ubuntu noob here (been using it for all of about 3 days), so go easy on me as I'm still not quite sure what I'm doing.

I was trying to move the launcher to the bottom using this tutorial here [http://shuffleos.com/4525/move-unity-3d-launcher-bottom-ubuntu-1110-unity-bottom-launcher/](http://shuffleos.com/4525/move-unity-3d-launcher-bottom-ubuntu-1110-unity-bottom-launcher/) all was going fine till I turned on unity rotated in CCSM, basically now I have a totally blank desktop with nothing at all showing :confused: I can even seem to get terminal to open using ctrl-alt-t

I can still login as rootwhich is fine, but I'd greatly appreciate it if someone could help me get un-screw up my desktop :lol:

---

### Post by DS McGuire on 2012-01-02
Do you have Ubuntu 2D on the login screen? If so login using that. 

I did something like this a few weeks ago, what I did:
logged into Ubuntu 2D from the login screen and go to compiz, go to preferences and change the profile to unity, made my changes using compiz, logged out and it was fine :)

Good luck :)

---

### Post by yugnip on 2012-01-02
It tells you how to remove the plugin at the end of the tutorial, and it seems pretty standard.

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:paullo612/unityshell-rotated
sudo apt-get remove unityshell-rotated
```

Of course if you can login as root, you won't need 'sudo' in front of each command.

---

### Post by littleport2003 on 2012-01-02
> **DS McGuire said:**
> Do you have Ubuntu 2D on the login screen? If so login using that. 

I did something like this a few weeks ago, what I did:
logged into Ubuntu 2D from the login screen and go to compiz, go to preferences and change the profile to unity, made my changes using compiz, logged out and it was fine :)

Good luck :)

Thanks for the quick reply, just logged into Ubuntu 2D and sorted it :D

> **yugnip said:**
> It tells you how to remove the plugin at the end of the tutorial, and it seems pretty standard.

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:paullo612/unityshell-rotated
sudo apt-get remove unityshell-rotated
```

Of course if you can login as root, you won't need 'sudo' in front of each command.

Like I said, total noob, wasn't sure if I could undo it from root, or if I needed to be logged in on my normal account, but thanks for the quick reply, all sorted now :D


Edit: How do I mark this thread solved?

---

### Post by Derek Karpinski on 2012-01-02
Use thread tools above your original post to mark as solved. :P

---

