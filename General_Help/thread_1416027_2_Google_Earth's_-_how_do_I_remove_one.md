---
title: "2 Google Earth's - how do I remove one?"
date: 2010-02-25
forum: General Help
---

### Post by ptrinder64 on 2010-02-25
Hey guys,

I think I may have a pretty unique problem here...

For some reason, a long time ago, I couldn't find Google Earth in Synaptic, and so went to the Google Earth site and downloaded the Linux version. Unfortunately after a while this version kept on coming up with a 'new version available go to x to download update' which didn't work when I clicked on the link.

After a while I decided to see if I could uninstall it from Synaptic and then reinstall it to get the updated version. Unfortunately whilst Google Earth was now there it wasn't installed so I selected to install it. Now I have two versions of Google Earth and would like to remove the non-Synaptic version of this - anyone got any ideas?

Thanks in advance!

---

### Post by PoHandle on 2010-02-25
Check to see if there is a */opt/google-earth* directory.  That's usually where the 'non-synaptic' Google Earth installs to.  If it is there, then you can run the uninstall script provided in that directory:```
/opt/google-earth/uninstall
```

I'm not sure, but you might need to be root to run the uninstall script.

---

### Post by Seanuntu on 2010-02-25
I am at work and stuck in front of a windows tube... but...

Launch the one you want to remove, once it is running open a terminal window and type 'ps -ef'.  This should show you all the running processes.  Look for one that resembles Google Earth.  Is should have a path to the process that is running:

/opt/google/earth/googleearth or something like that.  Once you get that path you can look around in there and see if there is an uninstall script.

If there is no uninstall script, you should be able to just delete the folder.

---

### Post by ptrinder64 on 2010-02-25
Perfect guys - I managed to dig out the uninstall script from your advice and as it was in my home folder there was no need to run it as root.

Thanks for your speediness!

---

