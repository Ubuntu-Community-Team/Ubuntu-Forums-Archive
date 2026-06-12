---
title: "what happened to scsiadd in natty?"
date: 2011-05-10
forum: General Help
---

### Post by billd42 on 2011-05-10
What happened to the package 'scsiadd' in natty?  It seems to have been removed.  I have an external SATA HD dock and it was darned convenient for hotplugging drives in and out of it.  Thanks.

---

### Post by zukakog on 2011-05-28
It seems to have been removed because it wasn't working with the current kernels, according to [this]("https://launchpad.net/ubuntu/natty/amd64/scsiadd") post. You'll have to expand the publishing history to read the comments.

It also says that a replacement exists, but I can't find more info on it. Does anyone else know of an alternative to scsiadd? I use this all the time.

Thanks!

---

### Post by jthighlander on 2011-06-10
You may pick up the natty version of the package from here:  [https://launchpad.net/ubuntu/natty/+package/scsiadd](https://launchpad.net/ubuntu/natty/+package/scsiadd)

I'm just not sure why it's not in the repository.

---

### Post by billd42 on 2011-10-04
Sorry to resurrect this thread, but I finally answered my own question after all this while.

Seems that scsiadd was deprecated in the debian release on which natty is based because it uses because it uses the legacy /proc/scsi interface, which is now deprecated.  [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522542]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=522542") has more info.

The package to use in natty (and presumably oneiric et. seq. as well) is [scsitools]("https://launchpad.net/ubuntu/natty/+package/scsitools").  Just installed it, have yet to figure out how it works, but it looks like "scsi-spin(8)" will do what I want, namely spin a scsi HD up and down.

Hope this info is of use to someone else.

---

