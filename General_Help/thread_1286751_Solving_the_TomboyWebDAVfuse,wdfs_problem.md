---
title: "Solving the Tomboy/WebDAV/fuse,wdfs problem"
date: 2009-10-09
forum: General Help
---

### Post by jakev383 on 2009-10-09
I just went through this and now have it working, so I'd like to post how I got it working before closing all my tabs ;)

For those who have tried to sync their Tomboy notes over WebDAV, you'll see errors about fuse not being installed, wdfs not being available, etc. They're pretty easy fixes now (much harder when the option was first available in Tomboy - WHY HAVEN'T THEY BEEN FIXED IN THE REPOS YET?!?!?!?!!? :confused: ).
Anyway, assuming you have a WebDAV somewhere to sync to, the first thing you need to do is get some underlying programs installed. Follow the directions on this page:
```

[http://live.gnome.org/SeanFritz/UbuntuGutsyTomboySync](http://live.gnome.org/SeanFritz/UbuntuGutsyTomboySync)

```

I know, they're old instructions, but wdfs has not had an update since then so you're good. Get it all installed, yourself added to the group (in the instructions, replace "user" with your username), log out, and then log back in to apply the group changes. We're almost there.

Now that fuse is included in the kernel and is no longer a module, the Tomboy source needs to be modified to check for this. There is a patch available in the upstream, but it has not made it to the repos yet (see [https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/345166](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/345166)).

Bryan has been nice enough to patch Tomboy in his PPA and make it available, so add his PPA to your /etc/apt/sources.list file for your architecture (I'm using amd64, but I know there are 32-bit packages as well). Bryan's PPA page is here:
```

[https://edge.launchpad.net/~brywilharris/+archive/ppa](https://edge.launchpad.net/~brywilharris/+archive/ppa)

```

Once you have his PPA installed in your sources.list file, simple:
```

sudo apt-get update
sudo apt-get install tomboy

```

This will install the patched version of Tomboy for you, and you should be good after that. I performed a reboot myself at this point, but you may not need to.

Hope this helps someone else!

---

### Post by mingsos on 2009-10-26
It works!

Thanks, you rock :guitar:

---

### Post by jakev383 on 2009-10-27
No problem. Glad it helped! :D

---

### Post by shrodi on 2010-05-12
It doesn't seem wdfs related, but is anyone experimenting the following TomBoy WebDAV sync bug in Lucid?

[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/575061](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/575061)

---

### Post by morgainebrigid on 2010-06-16
Thanks!

---

### Post by connermcd on 2010-08-29
> **shrodi said:**
> It doesn't seem wdfs related, but is anyone experimenting the following TomBoy WebDAV sync bug in Lucid?

[https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/575061](https://bugs.launchpad.net/ubuntu/+source/tomboy/+bug/575061)

Yes, I'm having the exact same problem.

---

