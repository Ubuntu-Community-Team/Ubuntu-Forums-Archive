---
title: "Connect Windows Mobile to Ubuntu 11.04"
date: 2011-05-09
forum: General Help
---

### Post by herpez on 2011-05-09
Hi!
I'm trying to connect my windows mobile 6 phone to my ubuntu.

In **10.10** i followed this tutorial: 
[http://ubuntuforums.org/showthread.php?t=1475888](http://ubuntuforums.org/showthread.php?t=1475888)

and all went good. As in that tutorial, i tried to install those packets:
[B]opensync-plugin-synce
synce-gvfs
synce-trayicon
[/B]
Well, synce-gvfs and synce-trayicon went fine, but **opensync-plugin-synce came with error**:
```
Some packages could not be installed. This may mean that you have requested an impossible 
situation or if you are using the unstable distribution that some required packages have
not yet been created or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 opensync-plugin-synce : Depends: opensync-module-python but it is not installable
E: Broken packages
```

When i try to install opensync-module-python it says:
```
Package opensync-module-python is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'opensync-module-python' has no installation candidate
```

I appreciate your help.

Thanks!

---

### Post by Doj on 2011-07-25
For those still struggling, this is what you do:


You'll need to download the dependency:
[http://packages.debian.org/sid/opensync-module-python]("http://packages.debian.org/sid/opensync-module-python")

This needs libopensync0, findable here:
[http://packages.ubuntu.com/hardy/libopensync0]("http://packages.ubuntu.com/hardy/libopensync0")

For this to be installed, you'll need python 2.5, instructions for installing can be found here:
[http://efreedom.com/Question/6-40279/Possible-Install-Python-25-1104]("http://efreedom.com/Question/6-40279/Possible-Install-Python-25-1104://")


I've just been trying this myself, so I can't guarantee if it will work... I still have to log out and log back in.

Hope it works for you, last time I couldn't get it to work on my SE X1...


One more thing: you'll need to enable all apps to use the unity tray, though i forgot how to now, google has the answers... or you could just use gnome 2 instead of unity...

---

