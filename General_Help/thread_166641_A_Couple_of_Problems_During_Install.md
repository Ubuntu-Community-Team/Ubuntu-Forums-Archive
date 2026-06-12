---
title: "A Couple of Problems During Install"
date: 2006-04-26
forum: General Help
---

### Post by hawque on 2006-04-26
I just picked up an Acer Aspire 5003WLMI notebook. After getting it home, I downloaded an Install CD of Breezy Badger, of the AMD64 variety. When it first boots from the CD, it's fine. However, once I tell it to 'install,' and it changes to the blue installation screen there is a horizontal black bar near the top of the screen. Above that is what should be at the very bottom of my screen.

Since this only seemed to be a problem during the installation (as it didn't give me that bar at first - and hasn't since, while shutting down for me to reset), I figured it might fix itself when everything was up and running.

Well, I haven't gotten that far yet. I manage to navigate through the prompts and get to installing the base system, when it comes up with an error telling me that it is unable to install the selected kernel (linux-amd64-generic). I've seen a similar error on my Desktop before, but that ended up being because of some bad RAM. Any ideas as to what is causing either of these problems, and how to fix them?

---

### Post by hawque on 2006-04-27
Well, the major problem was something that was just stupid of me to miss - my CD was bad. I reburned it and the install has been working like a champ since I restarted it.

However, I'm not so sure that the black bar is going to be so easy. It's still there, and after I reset and removed the CD it still appeared during the Ubuntu loading screen, which I know should not be the case if it was, like I hoped, only a problem during installation.

From what I've searched, I realize this is probably fixable with some tweaking of my xorg.conf, but I haven't had much luck finding the values I need for the notebook.

Edit: GNOME doesn't seem to have a problem with it, but if I switch to a text prompt (Ctrl+Alt+F1, for instance) the bar is still there (though I can't see it, the prompt doesn't begin at the top of the screen). This is a much less urgent problem now, but I would still like to be able to fix it if possible.

---

