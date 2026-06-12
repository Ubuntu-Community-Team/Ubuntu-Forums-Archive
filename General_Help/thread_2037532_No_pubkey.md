---
title: "No_pubkey?"
date: 2012-08-04
forum: General Help
---

### Post by scottr99 on 2012-08-04
Hello, I recently started getting this message in my terminal:

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D8AD4DE78EEBB0CA

How can I fix/stop this, anyone?  Thank you.

---

### Post by drs305 on 2012-08-04
Are you using the Oneric repository? If so, you can add the key for the repository with this command:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 8EEBB0CA
```

---

### Post by scottr99 on 2012-08-04
Thank you, well I looked through my Update Manager and I don't see anything in there to indicate that I am using Oneric.  Is there something about it that makes it undesirable?  I'm a noob so idk.

I see Canonical in there too but it is not checked.

Thank you!

---

### Post by drs305 on 2012-08-04
You can check the release you are using with:
```

lsb_release -c
```

If it isn't Oneiric and you haven't knowingly tried to add it's repository, you can edit your repository list (/etc/apt/sources.list). You can do it via one of the GUI software installers. 

From Ubuntu Software Center, go to Edit, Software Sources, Other Software tab. Take a look for the one with "Oneiric" in the address. This is the one that is causing the key message you are seeing. If you untick it the next time you try to install an app or update the repository list it shouldn't try to access the Oneiric repository and the message will not appear.

If you are running Oneiric, then just run the command I posted earlier to add that key to your system.

---

### Post by scottr99 on 2012-08-04
I checked and I got this:

Codename:       precise

So it appears I am not using Oneiric.  But I already added the Oneiric key with the previous command before I saw your latest post.  I did an update and I didn't get a 'no_key' message so I guess the "sudo apt-key adv.." command fixed?  Can I just leave things as it, or should I go ahead and edit the repos list anyway?  Thank you again.

---

### Post by drs305 on 2012-08-04
Unless you knowingly added the Oneiric repository, I'd recommend deactivating it. You can just untick it but not delete it so you can restore it if you need to in the future for some reason.

The reason I'd remove it is that the Oneiric End of Life will occur much earlier than Precise, and when that happens the repository will be moved and you will get a 'not found' error when trying to update. 

There's no rush, as the Oneiric EOL is April 2013, but there isn't a need for it's repository. If you do happen to have an app which is relying on Oneiric, the app won't get any updates but otherwise will continue to work.

If you would like to see what, if any, apps are using the Oneiric repository, you can install 'synaptic' and then click the "Origin" bar in the left pane. If you can remember, sometimes a user will activate an older repository to be able to use a 3rd party app that hasn't been upgraded to the latest Ubuntu version.

Once you decide what to do and have no other questions please mark the thread "Solved" via the thread tools link near the top right of the original post.

---

### Post by scottr99 on 2012-08-04
Ok with Origin in Synaptic I now remember why it's there.  I installed Clipgrab from this site (half way down the page):

[http://www.liberiangeek.net/2012/04/tools-to-play-download-watch-youtube-videos-in-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/04/tools-to-play-download-watch-youtube-videos-in-ubuntu-12-04-precise-pangolin/)

and the directions instructed to create a temporary install of Oneiric.  So now I have no fear of unticking it.

Thank you very much! :)

---

