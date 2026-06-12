---
title: "Brasero Audio CD &quot;normalizing forever&quot; bug workaround"
date: 2009-11-07
forum: General Help
---

### Post by OrangeVixen on 2009-11-07
I figured out the problem with Brasero getting stuck forever at the "Normalizing" stage when burning Audio CDs.

If you go to Brasero's Edit->Plugins, you will find a Normalize plugin in the plugins list, disable it and you won't get stuck at that stage any more.

---

### Post by cascade9 on 2009-11-07
*blinks* I dont use Brasero, but IMO normalise shouldn't be turned on by default.

---

### Post by scallywagjazz on 2009-12-04
First post and still fiddling around, but must say Ubuntu 9.10 is superb on my Dell Latitude D610, super fast, stable, responsive and not getting clogged up with garbage.

Anyway, saw the normalize problem when creating a compilation CD. Stuck with the Normalize window status, zipping from side to side. 

Some various posts suggested installing K3b, which I did, and when attempting to the same Normalize operation in K3b, received a pop-up informing that a package 'normalize-audio' needs to be installed.

Used Synaptic to find the package and installed it, and repeated the K3b operation, which normalized the tracks and burnt the CD. K3b then crashed for some reason.

Wondered if Brasero needed the 'normalize-audio' package for the 'normalize plugin', so I retried burning a CD in Brasero, with 'Normalize-plugin' enabled and it whizzed through and worked correctly.

Not sure if K3b installs a hidden dependency for the Brasero plugin to work, or if it is the 'normalize-audio' package which is required, as I haven't uninstalled K3b yet.

Therefore, you could try installing 'normalize-audio' package from Synaptic. Then re-try Brasero.

If that doesn't work, then try installing K3b and re-try Brasero, as we will know if it's just missing 'normalize-audio', or missing a dependency which is installed when K3b is installed?

---

### Post by timfinley on 2010-11-26
I had the same problem but found that normalize-audio was installed. I found mp3roaster found in synaptic package manager fixed my problem.

---

